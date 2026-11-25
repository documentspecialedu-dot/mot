[akici_okuma2.html](https://github.com/user-attachments/files/35431993/akici_okuma2.html)
<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Akıcı Okuma Atölyesi – Alp'in Macerası</title>
<style>
:root{--blue:#2457c5;--navy:#172b4d;--bg:#f3f6fb;--muted:#64748b;--green:#16834a;--soft-blue:#0284c7;--line:#e3e9f2}
*{box-sizing:border-box}body{margin:0;background:var(--bg);font-family:Arial,sans-serif;color:var(--navy)}
header{background:#fff;border-bottom:1px solid var(--line);padding:18px 22px}
header .inner{max-width:1050px;margin:auto;display:flex;justify-content:space-between;align-items:center;gap:12px;flex-wrap:wrap}
h1{font-size:22px;margin:0;color:var(--blue)}.tag{font-size:12px;background:#eaf0ff;color:var(--blue);padding:7px 10px;border-radius:20px}
main{max-width:1050px;margin:24px auto;padding:0 16px}
.panel{background:#fff;border:1px solid var(--line);border-radius:18px;padding:20px;margin-bottom:16px;box-shadow:0 5px 18px #172b4d08}
.row{display:flex;gap:12px;align-items:center;flex-wrap:wrap}.between{justify-content:space-between}
label{font-size:13px;color:var(--muted);display:block;margin-bottom:6px}
input,select,textarea{font:inherit;border:1px solid #ccd5e3;border-radius:10px;padding:11px;background:#fff;color:var(--navy);width:100%}
.field{flex:1;min-width:180px}button{border:0;border-radius:11px;padding:11px 16px;font-weight:700;cursor:pointer;background:var(--blue);color:white;transition:0.2s}
button:hover{opacity:0.9}
button.secondary{background:#e9eef7;color:var(--navy)}button.green{background:var(--green)}button.red{background:#fff0f0;color:#c93434}button:disabled{opacity:.45;cursor:not-allowed}
.tabs{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin-bottom:16px}
.tab{background:#e8edf6;color:#334155;padding:13px 8px}.tab.active{background:var(--blue);color:#fff}
.stage{display:none}.stage.active{display:block}
.kicker{font-size:12px;color:var(--muted);text-transform:uppercase;letter-spacing:.08em;font-weight:bold}
.prompt{font-size:clamp(34px,7vw,58px);font-weight:800;letter-spacing:2px;text-align:center;margin:25px 0;color:#14284a;overflow-wrap:anywhere}
.instructions{text-align:center;color:var(--navy);line-height:1.6;font-size:16px;background:#eef4ff;padding:12px;border-radius:10px;margin-bottom:20px;}
.status{text-align:center;min-height:28px;margin:15px 0;font-weight:700}
.feedback{text-align:center;background:#f6f8fc;border-radius:12px;padding:14px;min-height:60px;line-height:1.6}
.good{color:var(--green);font-weight:bold}.uncertain{color:var(--soft-blue);font-weight:bold}
.small{font-size:12px;color:var(--muted);line-height:1.5}
.stats{display:flex;gap:10px;flex-wrap:wrap}.stat{background:#f4f7fc;border-radius:12px;padding:12px 16px;min-width:110px;flex:1;border:1px solid #e2e8f0;}
.stat b{display:block;font-size:22px;margin-top:4px}
hr{border:0;border-top:1px solid var(--line);margin:18px 0}
table{width:100%;border-collapse:collapse;font-size:13px}th,td{text-align:left;padding:9px;border-bottom:1px solid var(--line)}th{color:var(--muted)}

#highlightedText { font-size: 22px; line-height: 1.9; background: #f7f9fd; padding: 20px; border-radius: 12px; margin: 20px 0; border: 1px solid var(--line); }
.word-correct { color: var(--green); font-weight: bold; display: inline-block; margin-right: 5px; }
.word-wrong { color: var(--soft-blue); font-weight: bold; display: inline-block; margin-right: 5px; background: #f0f9ff; padding: 0 4px; border-radius: 4px; }

.checklist-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-top: 12px; font-size: 14px; }
.checklist-item { display: flex; align-items: center; gap: 8px; background: #f8fafc; padding: 8px; border-radius: 8px; cursor:pointer; }
.checklist-item input { width: auto; }

#apiKeyContainer { background: #fff3cd; border-bottom: 1px solid #ffeeba; padding: 10px 22px; text-align: center; display: none; justify-content: center; align-items: center; gap: 10px; flex-wrap:wrap;}
#apiKeyInput { width: 300px; padding: 8px; border: 1px solid #ccc; border-radius: 6px; }
#saveApiKeyBtn { padding: 8px 16px; background: #ffc107; color: #000; border: none; border-radius: 6px; cursor: pointer; font-weight: bold; }
#clearApiKeyBtn { padding: 8px 16px; background: #dc3545; color: #fff; border: none; border-radius: 6px; cursor: pointer; font-weight: bold; }

@media(max-width:650px){.tabs{grid-template-columns:repeat(2,1fr)}.panel{padding:15px}.checklist-grid{grid-template-columns:1fr}}
</style>
</head>
<body>

<!-- Gemini API Anahtar Giriş Paneli -->
<div id="apiKeyContainer">
    <span>🔑 Gemini API Anahtarı:</span>
    <input type="password" id="apiKeyInput" placeholder="AQ... veya AIza... ile başlayan anahtarınızı buraya yapıştırın">
    <button id="saveApiKeyBtn">Kaydet</button>
    <button id="clearApiKeyBtn">Temizle/Sil</button>
</div>

<header>
    <div class="inner">
        <div>
            <h1>📘 Akıcı Okuma Atölyesi</h1>
            <span class="tag">MEB ÖGES Etkinlikleri & Gemini Ses Entegrasyonu</span>
        </div>
        <!-- API Anahtarı Butonu -->
        <button id="toggleApiKeyBtn" class="secondary" style="font-size:13px; padding:8px 12px;">🔑 API Anahtarını Ayarla</button>
    </div>
</header>

<main>
<section class="panel">
 <div class="row">
  <div class="field"><label for="student">Öğrenci adı</label><input id="student" value="Alp"></div>
  <div class="field"><label for="level">Çalışma düzeyi</label><select id="level"><option>Başlangıç</option><option>Gelişmekte</option><option>İlerleyen</option></select></div>
  <div class="field"><label for="sessionDate">Tarih</label><input id="sessionDate" type="date"></div>
 </div>
 <p class="small">Bu prototip tanı koymaz. Otomatik ses tanıma sonuçları öğretmen tarafından gözden geçirilmelidir. Seslendirme için Gemini yapay zekası kullanılmaktadır. Gemini API çalışmazsa otomatik olarak tarayıcı sesine geçilir.</p>
</section>

<nav class="tabs">
 <button class="tab active" data-tab="letters">1. Harf karıştırma</button>
 <button class="tab" data-tab="syllables">2. Hece okuma</button>
 <button class="tab" data-tab="words">3. Sözcük okuma</button>
 <button class="tab" data-tab="fluency">4. Okuma akıcılığı</button>
</nav>

<section id="letters" class="stage active panel">
 <div class="kicker">Bölüm 1 · Harf karıştırma</div>
 <p class="instructions">Merhaba <span class="studentName">Alp</span>! 🌟 Şimdi seninle <b>harfleri tanıma ve doğru seslendirme</b> etkinliği yapacağız. Ekrandaki harfi yüksek sesle oku, hadi başlayalım!</p>
 <div class="prompt" id="letterPrompt">b</div>
 <div class="row" style="justify-content:center">
  <button class="secondary" onclick="speakCurrent()">🔊 Dinle</button><button onclick="startMic()">🎤 Oku</button><button class="secondary" onclick="manualEntry()">✍️ Yazılı yanıt</button>
 </div>
 <div class="status" id="letterStatus">Hazır olduğunda oku.</div><div class="feedback" id="letterFeedback">Yanıtın burada gösterilecek.</div>
 <div class="row between" style="margin-top:14px"><button class="secondary" onclick="prevItem()">← Önceki</button><span id="letterCount" class="small">1 / 8</span><button class="green" onclick="nextItem()">Sonraki →</button></div>
</section>

<section id="syllables" class="stage panel">
 <div class="kicker">Bölüm 2 · Hece okuma</div>
 <p class="instructions">Harika gidiyorsun <span class="studentName">Alp</span>! 🚀 Şimdi <b>heceleri birleştirme</b> etkinliğine geçiyoruz. Ekrandaki heceyi sesli oku, bakalım ne kadar hızlı yapabileceksin!</p>
 <div class="prompt" id="syllablePrompt">ba</div>
 <div class="row" style="justify-content:center"><button class="secondary" onclick="speakCurrent()">🔊 Dinle</button><button onclick="startMic()">🎤 Oku</button><button class="secondary" onclick="manualEntry()">✍️ Yazılı yanıt</button></div>
 <div class="status" id="syllableStatus">Hazır olduğunda oku.</div><div class="feedback" id="syllableFeedback">Yanıtın burada gösterilecek.</div>
 <div class="row between" style="margin-top:14px"><button class="secondary" onclick="prevItem()">← Önceki</button><span id="syllableCount" class="small">1 / 8</span><button class="green" onclick="nextItem()">Sonraki →</button></div>
</section>

<section id="words" class="stage panel">
 <div class="kicker">Bölüm 3 · Sözcük okuma</div>
 <p class="instructions">Süpersin <span class="studentName">Alp</span>! 🎉 Şimdi <b>sözcük okuma</b> zamanı. Ekrandaki kelimeyi oku ve mikrofonu kullanarak bana sesini gönder.</p>
 <div class="prompt" id="wordPrompt">masa</div>
 <div class="row" style="justify-content:center"><button class="secondary" onclick="speakCurrent()">🔊 Dinle</button><button onclick="startMic()">🎤 Oku</button><button class="secondary" onclick="manualEntry()">✍️ Yazılı yanıt</button></div>
 <div class="status" id="wordStatus">Hazır olduğunda oku.</div><div class="feedback" id="wordFeedback">Yanıtın burada gösterilecek.</div>
 <div class="row between" style="margin-top:14px"><button class="secondary" onclick="prevItem()">← Önceki</button><span id="wordCount" class="small">1 / 8</span><button class="green" onclick="nextItem()">Sonraki →</button></div>
</section>

<section id="fluency" class="stage panel">
 <div class="kicker">Bölüm 4 · Okuma akıcılığı</div>
 <p class="instructions">Vay canına <span class="studentName">Alp</span>, artık koca bir metin okuyacaksın! 📖 Seninle <b>okuma akıcılığı</b> etkinliği yapacağız. Metni baştan sona oku. Okumayı bitirdiğinde sistem otomatik olarak duracak ve kelimeleri renklendirecek. Hazırsan başlayalım!</p>
 
 <div class="row" style="margin-bottom: 12px;">
    <div class="field">
        <label>Çalışılacak Metin</label>
        <select id="passageSelect" onchange="changePassage()">
            <option value="default">Varsayılan Kısa Metin</option>
            <option value="cikolata">Çikolata mı Kokolin mi? (ÖGES)</option>
            <option value="unutmusum">Unutmuşum (ÖGES)</option>
            <option value="minik_tavsan">Minik Tavşan (Kısa Metin)</option>
            <option value="aylar">Aylar ve Anlamları (Kısa Metin)</option>
            <option value="kucuk_kedi">Küçük Kedi (Kısa Metin)</option>
        </select>
    </div>
 </div>
 
 <div id="highlightedText">Metin buraya yüklenecek...</div>
 
 <div class="row" style="justify-content:center">
    <button class="secondary" onclick="speakCurrent()">🔊 Metni Dinle (Model Okuma)</button>
    <button onclick="startMic()">🎤 Metni Oku</button>
    <button class="secondary" onclick="manualEntry()">✍️ Yazılı yanıt</button>
 </div>
 
 <div class="stats" style="margin-top:16px">
    <div class="stat"><span class="small">Geçen süre</span><b id="elapsed">0 sn</b></div>
    <div class="stat"><span class="small">Toplam Kelime</span><b id="targetCount">0</b></div>
    <div class="stat"><span class="small">Doğru Okunan</span><b id="correctWords" style="color:var(--green)">0</b></div>
    <div class="stat"><span class="small">Hatalı Okunan</span><b id="wrongWords" style="color:var(--soft-blue)">0</b></div>
    <div class="stat"><span class="small">Doğruluk Yüzdesi</span><b id="accuracy" style="color:var(--blue)">0%</b></div>
 </div>
 
 <div class="status" id="fluencyStatus">Başlamak için oku düğmesine bas.</div>
 <div class="feedback" id="fluencyFeedback">Okuma tamamlandığında tanınan metin ve analiz burada görünür.</div>

 <hr>
 <b>📋 Kendini İzleme Kaba Değerlendirme Formu (ÖGES)</b>
 <p class="small">Etkinlik öncesi ve sonrasında kendini değerlendirmek için kutucukları işaretle.</p>
 <div class="checklist-grid">
     <label class="checklist-item"><input type="checkbox"> Okumaya başlamadan oturma pozisyonumu ayarladım.</label>
     <label class="checklist-item"><input type="checkbox"> Kitaba uygun mesafede oturdum.</label>
     <label class="checklist-item"><input type="checkbox"> Masa düzenimi sağladım.</label>
     <label class="checklist-item"><input type="checkbox"> Metni gözden geçirdim.</label>
     <label class="checklist-item"><input type="checkbox"> Okuma sonrası hatalarımı saydım.</label>
     <label class="checklist-item"><input type="checkbox"> Yaptığım hataları grafikte belirttim.</label>
 </div>
</section>

<section class="panel">
 <div class="row between"><div><b>🍩 Çaba puanları</b><div class="small">Tekrar denemek de öğrenmenin bir parçasıdır.</div></div><div style="font-size:28px">🍩 <b id="donuts">0</b></div></div>
 <hr>
 <div class="row between"><b>Oturum kayıtları</b><button class="secondary" onclick="exportCSV()">CSV indir</button></div>
 <div class="stats" style="margin:12px 0"><div class="stat"><span class="small">Deneme</span><b id="attempts">0</b></div><div class="stat"><span class="small">Doğru tanıma</span><b id="correct">0</b></div><div class="stat"><span class="small">Tekrar</span><b id="retries">0</b></div></div>
 <div style="overflow-x:auto"><table><thead><tr><th>Saat</th><th>Bölüm</th><th>Hedef</th><th>Tanılanan</th><th>Sonuç</th></tr></thead><tbody id="log"><tr><td colspan="5" class="small">Henüz kayıt yok.</td></tr></tbody></table></div>
</section>
<section class="panel">
 <b>Öğretmen içerik düzenleme</b>
 <p class="small">Aşağıdaki alanlara kendi öğretim planınıza göre hedefleri virgülle ayırarak yazabilirsiniz.</p>
 <div class="field"><label>Harf/hedef listesi</label><input id="editLetters" value="b,d,p,g,ğ"></div><br>
 <div class="field"><label>Hece listesi</label><input id="editSyllables" value="ba,be,bi,bo,bu,da,de,di"></div><br>
 <div class="field"><label>Sözcük listesi</label><input id="editWords" value="masa,kalem,kitap,elma,balık,çiçek,okul,araba"></div><br>
 <div class="field"><label>Varsayılan Akıcı Okuma Metni</label><textarea id="editPassage" rows="3">Ali sabah erkenden uyandı. Pencereden dışarı baktı. Bahçedeki kuşları gördü.</textarea></div><br>
 <button class="green" onclick="applyContent()">İçerikleri uygula</button>
</section>
</main>

<script>
// --- API ANAHTAR YÖNETİMİ ---
let geminiApiKey = "";
try {
    geminiApiKey = localStorage.getItem('geminiApiKey') || "";
} catch(e) {}

const apiKeyContainer = document.getElementById('apiKeyContainer');
const apiKeyInput = document.getElementById('apiKeyInput');
const saveApiKeyBtn = document.getElementById('saveApiKeyBtn');
const clearApiKeyBtn = document.getElementById('clearApiKeyBtn');
const toggleApiKeyBtn = document.getElementById('toggleApiKeyBtn');

// Başlangıçta anahtar yoksa paneli aç
if (!geminiApiKey || geminiApiKey.length < 10) {
    apiKeyContainer.style.display = 'flex';
    toggleApiKeyBtn.textContent = "🔑 API Anahtarını Gizle";
} else {
    apiKeyInput.value = geminiApiKey;
    toggleApiKeyBtn.textContent = "🔑 Anahtar Kayıtlı (Değiştir)";
}

toggleApiKeyBtn.addEventListener('click', () => {
    if (apiKeyContainer.style.display === 'none') {
        apiKeyContainer.style.display = 'flex';
        toggleApiKeyBtn.textContent = "🔑 API Anahtarını Gizle";
    } else {
        apiKeyContainer.style.display = 'none';
        toggleApiKeyBtn.textContent = "🔑 API Anahtarını Ayarla";
    }
});

saveApiKeyBtn.addEventListener('click', () => {
    const key = apiKeyInput.value.trim();
    if (!key) {
        alert("Lütfen geçerli bir API anahtarı girin.");
        return;
    }
    
    try {
        localStorage.setItem('geminiApiKey', key);
        geminiApiKey = key;
        alert("✅ API Anahtarı başarıyla kaydedildi!");
        apiKeyContainer.style.display = 'none';
        toggleApiKeyBtn.textContent = "🔑 Anahtar Kayıtlı (Değiştir)";
    } catch(e) {
        geminiApiKey = key;
        alert("⚠️ Anahtar geçici hafızaya kaydedildi. Sayfayı yenilerseniz silinir.");
        apiKeyContainer.style.display = 'none';
        toggleApiKeyBtn.textContent = "🔑 Anahtar Kayıtlı (Değiştir)";
    }
});

clearApiKeyBtn.addEventListener('click', () => {
    if(confirm("API anahtarını silmek istediğinize emin misiniz?")) {
        try {
            localStorage.removeItem('geminiApiKey');
        } catch(e) {}
        geminiApiKey = "";
        apiKeyInput.value = "";
        alert("Anahtar silindi. Tarayıcı sesi kullanılacak.");
        toggleApiKeyBtn.textContent = "🔑 API Anahtarını Ayarla";
    }
});


// --- VERİ VE METİNLER ---
const data = {
    letters: ["b","d","p","b","d","p","g","ğ"],
    syllables: ["ba","be","bi","bo","bu","da","de","di"],
    words: ["masa","kalem","kitap","elma","balık","çiçek","okul","araba"],
    passages: {
        default: "Ali sabah erkenden uyandı. Pencereden dışarı baktı. Bahçedeki kuşları gördü.",
        cikolata: "Bir çoğumuz çikolatayı severiz. Çikolatanın ham maddesi kakao çekirdeğidir. Kakao bitkisinin yetiştirilmesi için özel iklim koşullarına ihtiyaç vardır. Yani kakao ağacı her yerde yetişmez. Bu nedenle kakao, oldukça değerli ve pahalı bir bitkidir. Kakao, kakao yağı ve şeker çikolata yapımı için gereken temel malzemelerdir. Çikolatanın türüne göre bu maddelere çeşitli eklemeler yapılabilir. Örneğin temel malzemelere süt eklendiğinde sütlü çikolata elde edilir. Kokolin ise çikolataya çok benzer ancak farklı bir şekerleme türüdür. Maliyeti düşürmek için ürüne kakao yerine kakao tozu, süt yerine peynir altı suyu, kakao yağı yerine margarin veya sıvı yağ çeşitleri eklenir. Böylece ürün çikolataya benzeyen, düşük maliyetli bir şekerleme türüne dönüşür.",
        unutmusum: "Bazı şeyleri hatırlarım. Bazı şeyleri ise unuturum. Bu sabah dişlerimi fırçalamam gerektiğini hatırladım. Ama bulaşıkları lavaboya koymayı unuttum. Annem de beni bulaşıklar konusunda uyardı. Okul servisinin gelme vaktinde evin önündeydim ancak beslenme çantamı evde unutmuştum. Annem okula geldi ve bana yemeğimi getirdi. Eve döndüğümde okul kıyafetlerimi çıkardım ama çantamı yerine koymayı unuttum. Babam çantamı odama taşıdı ve ödevlerimi yapmam gerektiğini söyledi. Akşam yatmadan önce pijamalarımı giydim, sütümü içtim ve biraz kitap okudum. Annem odamın ışığını kapatacakken “Bir şey unutmadık değil mi?” diye sordum. Annem gülümsedi ve yanağıma bir öpücük kondurdu, “İyi geceler dilemeyi unuttun miniğim.” diye fısıldadı. Anneme iyi geceler diledim ve son sözü eklemeyi unutmadım: Güzel rüyalar gör.",
        minik_tavsan: "Minik tavşan ormanda neşeyle zıplıyordu. Aniden bir ses duydu. Bir yaprak hışırdadı. Korktu ve annesine doğru koştu. Annesi ona sarıldı ve 'Korkma yavrum, sadece rüzgardı' dedi. Minik tavşan rahatladı ve oyununa devam etti.",
        aylar: "Ocak ayında kar yağar. Şubat soğuk geçer. Mart'ta bahar gelir. Nisan yağmurları başlar. Mayıs çiçeklerle dolar. Haziran yazın başlangıcıdır. Temmuz sıcak, Ağustos kavurucudur. Eylül okulların açıldığı aydır. Ekim yaprakların döküldüğü, Kasım yağmurların başladığı aydır. Aralık ise yeni yılın müjdecisidir.",
        kucuk_kedi: "Küçük kedi bahçede oynuyordu. Bir kelebek gördü. Kelebeği yakalamak için zıpladı. Ama kelebek uçtu. Kedi üzülmedi. Çünkü arkadaşı köpek geldi. Birlikte koşup oynadılar."
    }
};

let currentPassageKey = "default";
let tab = "letters", indices = {letters:0, syllables:0, words:0}, donuts = 0, attempts = 0, correct = 0, retries = 0, logs = [];
let recognition = null, startedAt = null, timer = null, silenceTimeout = null;
let fallbackVoice = null;
let audioPlayer = null;

const studentInput = document.getElementById("student");
studentInput.addEventListener("input", (e) => {
    const name = e.target.value.trim() || "Alp";
    document.querySelectorAll(".studentName").forEach(el => el.textContent = name);
});

function loadVoices() {
    const voices = speechSynthesis.getVoices();
    fallbackVoice = voices.find(v => v.lang === 'tr-TR' && v.name.includes('Google')) 
                || voices.find(v => v.lang === 'tr-TR') 
                || voices.find(v => v.lang.startsWith('tr'));
}
speechSynthesis.onvoiceschanged = loadVoices;
loadVoices();

document.getElementById("sessionDate").value = new Date().toISOString().slice(0, 10);
const titles = { letters: "Harf karıştırma", syllables: "Hece okuma", words: "Sözcük okuma", fluency: "Okuma akıcılığı" };

document.querySelectorAll(".tab").forEach(b => b.addEventListener("click", () => switchTab(b.dataset.tab)));

function switchTab(t) {
    tab = t;
    document.querySelectorAll(".tab").forEach(b => b.classList.toggle("active", b.dataset.tab === t));
    document.querySelectorAll(".stage").forEach(s => s.classList.toggle("active", s.id === t));
    render();
}

function currentTarget() {
    if (tab === "fluency") return data.passages[currentPassageKey];
    return data[tab][indices[tab]];
}

function changePassage() {
    currentPassageKey = document.getElementById("passageSelect").value;
    render();
}

function render() {
    if (tab === "fluency") {
        const passage = data.passages[currentPassageKey];
        document.getElementById("highlightedText").textContent = passage;
        document.getElementById("targetCount").textContent = passage.split(/\s+/).length;
        document.getElementById("correctWords").textContent = "0";
        document.getElementById("wrongWords").textContent = "0";
        document.getElementById("accuracy").textContent = "0%";
        document.getElementById("fluencyFeedback").textContent = "Okuma tamamlandığında tanınan metin ve analiz burada görünür.";
        document.getElementById("fluencyStatus").textContent = "Başlamak için oku düğmesine bas.";
        return;
    }
    const target = currentTarget(), id = tab === "letters" ? "letter" : tab === "syllables" ? "syllable" : "word";
    document.getElementById(id + "Prompt").textContent = target;
    document.getElementById(id + "Count").textContent = (indices[tab] + 1) + " / " + data[tab].length;
    document.getElementById(id + "Status").textContent = "Hazır olduğunda oku.";
    document.getElementById(id + "Feedback").textContent = "Yanıtın burada gösterilecek.";
}

// --- GEMINI API İLE SESLENDİRME ---
async function speakCurrent() {
    let text = tab === "fluency" ? data.passages[currentPassageKey] : currentTarget();
    
    if (!geminiApiKey) {
        apiKeyContainer.style.display = 'flex'; // Paneli zorla aç
        alert("Gemini API anahtarı bulunamadı. Lütfen üstteki alandan anahtarınızı girip 'Kaydet' butonuna tıklayın.");
        return;
    }

    // Tarayıcının ses engelini aşmak için sessiz ses kilidi açma
    if (!audioPlayer) {
        const silentWav = "data:audio/wav;base64,UklGRigAAABXQVZFZm10IBIAAAABAAEARKwAAIhYAQACABAAAABkYXRhAgAAAAEA";
        audioPlayer = new Audio(silentWav);
    }
    audioPlayer.play().catch(e => console.log("Sessiz ses engellendi", e));

    setStatus("Ses oluşturuluyor...");
    const url = "https://generativelanguage.googleapis.com/v1beta/models/gemini-3.1-flash-tts-preview:generateContent";
    const payload = {
        contents: [{ parts: [{ text: text }] }],
        generationConfig: {
            responseModalities: ["AUDIO"],
            speechConfig: {
                voiceConfig: {
                    prebuiltVoiceConfig: { voiceName: "Kore" }
                }
            }
        }
    };

    try {
        const response = await fetch(url, {
            method: 'POST',
            headers: { 'Content-Type': 'application/json', 'x-goog-api-key': geminiApiKey },
            body: JSON.stringify(payload)
        });

        if (!response.ok) {
            const err = await response.json();
            throw new Error(err.error?.message || "Ses oluşturulamadı. Kotanızı veya anahtarınızı kontrol edin.");
        }

        const result = await response.json();
        let base64Audio = null;
        let mimeType = "audio/wav";
        
        if (result.candidates && result.candidates[0]?.content?.parts[0]?.inlineData) {
            base64Audio = result.candidates[0].content.parts[0].inlineData.data;
            if (result.candidates[0].content.parts[0].inlineData.mimeType) {
                mimeType = result.candidates[0].content.parts[0].inlineData.mimeType;
            }
        }

        if (base64Audio) {
            audioPlayer.src = `data:${mimeType};base64,${base64Audio}`;
            audioPlayer.play().then(() => {
                setStatus("Ses oynatılıyor...");
            }).catch(err => {
                throw new Error("Tarayıcı sesi oynatmayı reddetti.");
            });
        } else {
            throw new Error("Ses verisi yanıttan çıkarılamadı.");
        }
    } catch (error) {
        console.error("Gemini API Hatası:", error);
        alert("Gemini Ses Hatası: " + error.message + "\n\nTarayıcının kendi sesine geçiliyor...");
        fallbackSpeak(text);
    }
}

function fallbackSpeak(text) {
    let u = new SpeechSynthesisUtterance(text);
    u.lang = "tr-TR";
    if (fallbackVoice) u.voice = fallbackVoice;
    u.rate = 0.85;
    u.pitch = 1.1;
    speechSynthesis.cancel();
    speechSynthesis.speak(u);
    setStatus("Tarayıcı sesi oynatılıyor...");
}

// --- MİKROFON VE OTOMATİK DURDURMA ---
function startMic() {
    const SR = window.SpeechRecognition || window.webkitSpeechRecognition;
    if (!SR) {
        alert("Bu tarayıcıda konuşma tanıma bulunamadı. Lütfen güncel bir Google Chrome kullanın.");
        return;
    }
    if (recognition) { try { recognition.abort(); } catch(e){} }
    
    recognition = new SR();
    recognition.lang = "tr-TR";
    recognition.continuous = true; 
    recognition.interimResults = false;
    
    startedAt = Date.now();
    setStatus("Mikrofon açık: şimdi oku. (3 saniye sessizlikte otomatik durur)");
    
    if (tab === "fluency") {
        document.getElementById("elapsed").textContent = "Okunuyor…";
        timer = setInterval(() => {
            document.getElementById("elapsed").textContent = Math.floor((Date.now() - startedAt) / 1000) + " sn";
        }, 500);
    }

    let finalTranscript = "";

    recognition.onresult = e => {
        clearTimeout(silenceTimeout);
        for (let i = e.resultIndex; i < e.results.length; ++i) {
            if (e.results[i].isFinal) {
                finalTranscript += e.results[i][0].transcript + ' ';
            }
        }
        
        silenceTimeout = setTimeout(() => {
            if (recognition) recognition.stop();
        }, 3000);
    };

    recognition.onerror = e => {
        setStatus("Ses tanıma hatası: " + e.error);
        stopTimer();
    };

    recognition.onend = () => {
        stopTimer();
        if (finalTranscript.trim().length > 0) {
            processAnswer(currentTarget(), finalTranscript.trim());
        } else {
            setStatus("Ses algılanamadı. Lütfen tekrar deneyin.");
        }
    };

    try {
        recognition.start();
    } catch(e) {
        setStatus("Mikrofon başlatılamadı. İzinleri kontrol edin.");
    }
}

function stopTimer() {
    if (timer) { clearInterval(timer); timer = null; }
    if (startedAt) {
        const elapsed = Math.floor((Date.now() - startedAt) / 1000);
        if (tab === "fluency") document.getElementById("elapsed").textContent = elapsed + " sn";
    }
    clearTimeout(silenceTimeout);
}

function setStatus(s) {
    const id = tab === "fluency" ? "fluency" : tab === "letters" ? "letter" : tab === "syllables" ? "syllable" : "word";
    document.getElementById(id + "Status").textContent = s;
}

// --- KELİME KARŞILAŞTIRMA VE RENKLENDİRME ---
function evaluateReading(target, heard) {
    const tWords = target.split(/\s+/);
    const hWords = heard.toLowerCase().replace(/[.,!?;:]/g, "").split(/\s+/).filter(Boolean);
    
    let hIndex = 0;
    let correctCount = 0;
    let html = "";

    for (let i = 0; i < tWords.length; i++) {
        const tWord = tWords[i];
        const cleanTWord = tWord.toLowerCase().replace(/[.,!?;:]/g, "");
        
        let found = false;
        for (let j = hIndex; j < Math.min(hIndex + 3, hWords.length); j++) {
            if (hWords[j] === cleanTWord) {
                found = true;
                hIndex = j + 1; 
                break;
            }
        }
        
        if (found) {
            html += `<span class="word-correct">${tWord}</span> `;
            correctCount++;
        } else {
            html += `<span class="word-wrong">${tWord}</span> `;
        }
    }
    
    const wrongCount = tWords.length - correctCount;
    const accuracy = tWords.length > 0 ? Math.round((correctCount / tWords.length) * 100) : 0;
    
    return { html, correctCount, wrongCount, accuracy };
}

function processAnswer(target, heard) {
    attempts++;
    
    if (tab === "fluency") {
        const result = evaluateReading(target, heard);
        document.getElementById("highlightedText").innerHTML = result.html;
        document.getElementById("correctWords").textContent = result.correctCount;
        document.getElementById("wrongWords").textContent = result.wrongCount;
        document.getElementById("accuracy").textContent = result.accuracy + "%";
        
        document.getElementById("fluencyFeedback").innerHTML = `<b>Tanılanan konuşma:</b> ${heard}`;
        document.getElementById("fluencyStatus").textContent = "Harika iş çıkardın! Öğretmeninle birlikte renkli kelimeleri inceleyebilirsiniz.";
        
        logs.push({
            time: new Date().toLocaleTimeString("tr-TR"),
            section: titles[tab],
            target: target.substring(0, 25) + "...", 
            heard: heard.substring(0, 25) + "...",
            result: `%${result.accuracy} Başarı (D:${result.correctCount} / Y:${result.wrongCount})`
        });
        donuts++;
        document.getElementById("donuts").textContent = donuts;

    } else {
        const exact = norm(target) === norm(heard);
        const id = tab === "letters" ? "letter" : tab === "syllables" ? "syllable" : "word";
        
        document.getElementById(id + "Feedback").innerHTML = exact 
            ? '<span class="good">Eşleşti! Güzel deneme.</span>' 
            : '<span class="uncertain">Sistem hedefle aynı ifadeyi tanımadı.</span> Doğru örneği dinle ve yeniden dene.';
        document.getElementById(id + "Status").textContent = exact ? "Hedef ifadeyle eşleşti." : "Tekrar deneyebilirsin.";
        
        if (exact) { correct++; donuts++; document.getElementById("donuts").textContent = donuts; }
        else { retries++; }
        
        const result = exact ? "Eşleşti" : "Eşleşmedi";
        logs.push({time: new Date().toLocaleTimeString("tr-TR"), section: titles[tab], target, heard, result});
    }
    
    updateStats();
    renderLog();
}

function norm(s) {
    return (s || "").toLocaleLowerCase("tr-TR").replace(/[.,!?;:]/g, " ").replace(/\s+/g, " ").trim();
}

function manualEntry() {
    const val = prompt("Çocuğun okuduğunu düşündüğünüz ifadeyi yazın:");
    if (val !== null) processAnswer(currentTarget(), val);
}

function nextItem() {
    if (tab === "fluency") return;
    indices[tab] = (indices[tab] + 1) % data[tab].length; render();
}

function prevItem() {
    if (tab === "fluency") return;
    indices[tab] = (indices[tab] - 1 + data[tab].length) % data[tab].length; render();
}

function updateStats() {
    document.getElementById("attempts").textContent = attempts;
    document.getElementById("correct").textContent = correct;
    document.getElementById("retries").textContent = retries;
}

function renderLog() {
    const body = document.getElementById("log");
    body.innerHTML = "";
    if (logs.length === 0) {
        body.innerHTML = '<tr><td colspan="5" class="small">Henüz kayıt yok.</td></tr>';
        return;
    }
    logs.slice().reverse().forEach(x => {
        let tr = document.createElement("tr");
        [x.time, x.section, x.target, x.heard, x.result].forEach(v => {
            let td = document.createElement("td");
            td.textContent = v;
            tr.appendChild(td);
        });
        body.appendChild(tr);
    });
}

function exportCSV() {
    if (!logs.length) { alert("Henüz kayıt yok."); return; }
    const rows = [["Saat","Bölüm","Hedef","Tanılanan","Sonuç"], ...logs.map(x => [x.time, x.section, x.target, x.heard, x.result])];
    const csv = "\uFEFF" + rows.map(r => r.map(v => '"' + String(v).replace(/"/g, '""') + '"').join(";")).join("\n");
    const a = document.createElement("a");
    a.href = URL.createObjectURL(new Blob([csv], {type: "text/csv;charset=utf-8"}));
    a.download = "alp_okuma_oturumu.csv";
    a.click();
    URL.revokeObjectURL(a.href);
}

function applyContent() {
    const parse = id => document.getElementById(id).value.split(",").map(x => x.trim()).filter(Boolean);
    data.letters = parse("editLetters");
    data.syllables = parse("editSyllables");
    data.words = parse("editWords");
    data.passages.default = document.getElementById("editPassage").value.trim();
    
    if (currentPassageKey === "default") {
        data.passages.default = document.getElementById("editPassage").value.trim();
    }
    indices = {letters:0, syllables:0, words:0};
    render();
    alert("Yeni içerikler başarıyla uygulandı.");
}

render();
</script>
</body>
</html>
