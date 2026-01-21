[index.html](https://github.com/user-attachments/files/24756631/index.html)
<!DOCTYPE html>
<html lang="cs">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>J&T Stavebnictví</title>
<style>
body {
    margin: 0;
    font-family: Arial, sans-serif;
    background-color: #000;
    color: #fff;
}

/* Horní černý pruh s logem */
.header-strip {
    width: 100%;
    height: 150px;
    background-color: #000;
    display: flex;
    align-items: center;
    justify-content: center;
}
.header-strip .logo {
    max-height: 130px;
    max-width: 80%;
    object-fit: contain;
}

/* Menu - sticky */
nav {
    display: flex;
    justify-content: center;
    background-color: #111;
    padding: 15px 0;
    position: sticky;
    top: 0;
    z-index: 1000;
}
nav a {
    color: #fff;
    text-decoration: none;
    margin: 0 20px;
    font-weight: bold;
    transition: color 0.3s;
}
nav a:hover { color:#c1121f; }

/* Hlavní obsah */
.container {
    max-width: 1000px;
    margin: 20px auto 80px;
    background-color: #333;
    padding: 40px;
    border-radius: 12px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.3);
}

/* O NÁS */
.about-title { color:#c1121f; font-size:24px; margin-bottom:10px; }
.about-text p { color:#ddd; line-height:1.6; margin-bottom:15px; }

/* Fotky služeb */
.section-title { color:#c1121f; font-size:24px; margin-bottom:20px; text-align:center; }
.items { display:flex; flex-wrap:wrap; gap:20px; justify-content: space-between; margin-bottom:40px; }
.item { flex: 1 1 30%; background:#444; border-radius:8px; overflow:hidden; text-align:center; transition: transform 0.3s, box-shadow 0.3s; }
.item:hover { transform: translateY(-5px); box-shadow: 0 8px 15px rgba(0,0,0,0.4); }
.item img { width:100%; height:250px; object-fit:cover; display:block; }
.item h3 { color:#c1121f; margin:10px 0 5px 0; }
.item p { color:#ddd; margin:0 0 15px 0; }

/* Červený blok Reference – přes celou šířku */
.red-block {
    width: 100%;
    background-color: #c1121f;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 18px;
    color: #000;
    font-weight: bold;
    margin: 0 0 40px;
    border-radius: 0;
    padding: 15px 0;
}

/* Extra služby - 6 bloků */
.extra-services {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
    margin: 40px 0;
}
.extra-services .service-block {
    flex: 1 1 30%;
    background-color: #444;
    padding: 20px;
    border-radius: 8px;
    transition: transform 0.3s, box-shadow 0.3s;
}
.extra-services .service-block:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 15px rgba(0,0,0,0.4);
}
.extra-services h3 { color:#c1121f; margin-bottom:10px; }
.extra-services p { color:#ddd; margin-bottom:10px; }
.extra-services ul { list-style:none; padding-left:0; }
.extra-services ul li { position:relative; padding-left:20px; margin-bottom:5px; color:#ddd; }
.extra-services ul li::before { content:"–"; position:absolute; left:0; color:#c1121f; font-weight:bold; }

/* Kontaktní sekce */
.contact-section {
    display: flex;
    gap: 20px;
    flex-wrap: wrap;
    margin-top: 40px;
}
.contact-form-column,
.recommendation-column { flex:1; min-width:300px; }

/* Rámeček doporučení s carousel – výška poloviční a zlaté hvězdičky */
.recommendation {
    background-color: #c1121f;
    color: #000;
    padding: 15px 20px;
    border-radius: 12px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.3);
    font-size: 16px;
    line-height: 1.6;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 50%;
    position: relative;
}
.stars {
    color: gold;
    font-size: 18px;
    margin-bottom:10px;
}
.carousel-buttons { display:flex; justify-content:center; margin-top:15px; gap:10px; }
.carousel-buttons button { background:#a10f1a; color:#fff; border:none; padding:5px 12px; cursor:pointer; border-radius:5px; }
.recommendation .author { font-weight:bold; font-size:16px; margin-top:10px; }

/* Formulář */
.contact-form input, .contact-form textarea { width:100%; padding:10px; margin-bottom:15px; border-radius:5px; border:none; }
.contact-form button { background:#c1121f; color:#000; font-weight:bold; padding:15px 20px; border:none; border-radius:8px; cursor:pointer; }
.contact-form button:hover { background:#a10f1a; }

/* Popup potvrzení */
#form-popup {
    display:none;
    position: fixed;
    top:50%;
    left:50%;
    transform: translate(-50%, -50%);
    background:#c1121f;
    color:#000;
    padding:20px 40px;
    border-radius:10px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.5);
    font-size:18px;
    z-index:2000;
}

/* Footer */
.footer-container { width:100%; background:#111; color:#ccc; text-align:center; padding:10px 0; font-size:14px; }
.footer-container a { color:#ccc; text-decoration:underline; }

/* Map iframe – užší */
.footer-map { max-width: 1000px; margin: 0 auto; }
.footer-map iframe { width:100%; height:200px; border:none; margin-bottom:10px; }

/* Responzivita */
@media(max-width:1024px){
    .container { padding:30px; }
    .item img { height:220px; }
    .recommendation { padding:15px 20px; }
}
@media(max-width:900px){
    .extra-services .service-block { flex:1 1 45%; }
    .items .item { flex:1 1 45%; }
}
@media(max-width:600px){
    .container { padding:20px; }
    .extra-services .service-block { flex:1 1 100%; }
    .items .item { flex:1 1 100%; margin-bottom:20px; }
    .contact-section { flex-direction: column; }
    .recommendation { height: auto; } 
}
@media(max-width:400px){
    nav a { margin: 0 10px; font-size:14px; }
    .section-title { font-size:20px; }
    .about-title { font-size:20px; }
    .recommendation { font-size:14px; }
}
</style>
</head>
<body>

<!-- Horní pruh s logem -->
<div class="header-strip">
    <img class="logo" src="images/logo.png" alt="J&T Stavebnictví Logo">
</div>

<!-- Menu -->
<nav>
    <a href="#about">O nás</a>
    <a href="#services">Služby</a>
    <a href="#references">Reference</a>
    <a href="#extra-services">Další služby</a>
    <a href="#contact">Kontakt</a>
</nav>

<div class="container">

<!-- O NÁS -->
<h2 class="about-title">O NÁS:</h2>
<div class="about-text" id="about">
<p>J&T Stavebnictví působí na trhu již mnoho let a získala si reputaci díky kvalitě, spolehlivosti a osobnímu přístupu ke každému klientovi. Naše specializace zahrnuje kompletní realizace cihlových domů, rekonstrukce, zateplení a fasády, přičemž vždy dbáme na detail a estetický vzhled.</p>
<p>Náš tým tvoří zkušené zedníky a stavební odborníky, kteří kombinují tradiční řemeslnou dovednost s moderními stavebními technologiemi. Každý projekt je pro nás unikátní a přistupujeme k němu s maximální pečlivostí, aby výsledná stavba splňovala nejvyšší standardy kvality a bezpečnosti.</p>
<p>Naším cílem je spokojený zákazník – proto dbáme nejen na precizní provedení, ale i na rychlost a efektivitu prací. Spolu s vámi plánujeme a realizujeme každý projekt od prvotního návrhu až po finální dokončení, abyste se mohli těšit z nového či zrekonstruovaného domu, který vydrží generace.</p>
</div>

<!-- Fotky služeb -->
<div id="services">
<h2 class="section-title">Služby</h2>
<div class="items">
    <div class="item">
        <img src="images/foto1.jpg" alt="Co děláme">
        <h3>Co děláme</h3>
        <p>Zateplení, stavby domu, rekonstrukce, novostavby, fasády</p>
    </div>
    <div class="item">
        <img src="images/foto2.jpg" alt="Na trhu">
        <h3>Na trhu</h3>
        <p>Již několik let poskytujeme kvalitní stavební služby s maximální spokojeností zákazníků</p>
    </div>
    <div class="item">
        <img src="images/foto3.jpg" alt="Naše služby">
        <h3>Naše služby</h3>
        <p>Novostavby a rekonstrukce cihlových domů s profesionálním zateplením a fasádou</p>
    </div>
</div>
</div>

<!-- Červený blok Reference – přes celou šířku -->
<div id="references" class="red-block">
Reference – viz naše realizace
</div>

<!-- Extra služby (6 bloků) -->
<div id="extra-services" class="extra-services">
<div class="service-block">
<h3>STAVEBNÍ PRÁCE & VÝSTAVBY</h3>
<p>Komplexní stavební služby od projektu až po dokončení. Novostavby, rekonstrukce, dokončovací práce.</p>
<ul>
<li>Výstavbu rodinných domů a přestavby budov</li>
<li>Základová deska</li>
<li>Izolace domu proti vlhkosti</li>
<li>Půdní výstavby</li>
</ul>
</div>

<div class="service-block">
<h3>REKONSTRUKCE & REVITALIZACE</h3>
<p>Proměňte svůj dům nebo byt s našimi profesionálními rekonstrukcemi a revitalizacemi.</p>
<ul>
<li>Rekonstrukce bytů</li>
<li>Rekonstrukce rodinných domů</li>
<li>Rekonstrukce komerčních staveb</li>
<li>Rekonstrukce bytových jader</li>
<li>Rekonstrukce chat a chalup</li>
</ul>
</div>

<div class="service-block">
<h3>ZEDNICKÉ PRÁCE</h3>
<p>Odborné provádění zednických prací od opravy zdí až po jejich výstavbu.</p>
<ul>
<li>Štukování, omítání a oprava zdí a stěn</li>
<li>Natažení stěn lepidlem s perlinkou</li>
<li>Průmyslové betonové podlahy a nivelace</li>
<li>Zdění z cihel a tvárnic</li>
<li>Dekorativní a betonové štěrky</li>
</ul>
</div>

<div class="service-block">
<h3>SÁDROKARTONÁŘSKÉ PRÁCE</h3>
<p>Sádrokartonové práce pro profesionální vzhled interiéru - od instalace až po finální úpravy.</p>
<ul>
<li>Sádrokartonové podhledy</li>
<li>Sádrokartonové příčky</li>
<li>Sádrokartonové předstěny a kastlíky</li>
<li>Sádrokartonové kazetové podhledy</li>
</ul>
</div>

<div class="service-block">
<h3>DEMOLIČNÍ PRÁCE</h3>
<p>Nabízíme kompletní řešení - od bourání až po konečné odstranění.</p>
<ul>
<li>Bourací práce a vyklízení</li>
<li>Demolice</li>
<li>Zemní a výkopové práce</li>
<li>Likvidace odpadů a sutí</li>
</ul>
</div>

<div class="service-block">
<h3>DRENÁŽE & ODVODNĚNÍ</h3>
<p>Drenáže a odvodnění jsou klíčovým faktorem pro udržení sucha a stability ve vaší stavbě. S pečlivým přístupem a důrazem na efektivitu provedu drenážní opatření, která zajistí odpovídající odvodnění a ochranu vaší konstrukce před vlhkostí.</p>
</div>
</div>

<!-- Kontaktní sekce s doporučením -->
<div id="contact" class="contact-section">
  <div class="recommendation-column">
    <div class="recommendation" id="recommendation">
      <div class="stars">★★★★★</div>
      <p id="rec-text"></p>
      <div class="author" id="rec-author"></div>
      <div class="carousel-buttons">
        <button onclick="showRec(0)">1</button>
        <button onclick="showRec(1)">2</button>
        <button onclick="showRec(2)">3</button>
      </div>
    </div>
  </div>
  <div class="contact-form-column contact-form">
    <h2>Kontaktujte nás</h2>
    <form id="contactForm" action="https://formspree.io/f/xlggedqz" method="POST">
      <input type="text" name="name" placeholder="Vaše jméno" required>
      <input type="email" name="email" placeholder="Váš email" required>
      <input type="text" name="phone" placeholder="Telefon">
      <textarea name="message" placeholder="Vaše zpráva" rows="6" required></textarea>
      <button type="submit">Odeslat zprávu</button>
    </form>
  </div>
</div>

<!-- Mapa -->
<div class="footer-map">
<iframe src="https://www.google.com/maps?q=Jana+Žižky+349,+Telč&output=embed"></iframe>
</div>

<!-- Footer -->
<div class="footer-container">
©2026 Zednické práce J&T Stavebnictví | Všechna práva vyhrazena | Osoba zapsána v živnostenském rejstříku | IČ: 60542918 | <a href="gdpr.html">GDPR</a>
</div>

</div>

<script>
// Carousel s hvězdičkami a recenzemi
const recs = [
  { text:"Chcela bych doporučit firmu J&T Stavebnictví na rekonstrukci bytů či domu. Musím ocenit profesionální přístup. Firma nám vyšla ve všem vstříc a na všem na čem jsme se domluvili tak to tak bylo. Rekonstrukce byla zhotovena včas podle smlouvy. Bylo potěšením s Vámi spolupracovat. Kvalita/spolehlivost.", author:"Bartáková P." },
  { text:"Velmi spokojený zákazník. Práce provedena profesionálně, všechny dohody byly dodrženy. Spolupráce s firmou byla bezproblémová a kvalitní.", author:"Novák J." },
  { text:"Doporučuji firmu J&T Stavebnictví. Kvalita, rychlost a precizní provedení všech prací byly skvělé. Tým je profesionální a spolehlivý.", author:"Svoboda M." }
];

function showRec(index){
  document.getElementById("rec-text").innerText = recs[index].text;
  document.getElementById("rec-author").innerText = recs[index].author;
}

// Inicializace první recenze
showRec(0);
</script>
</body>
</html>
