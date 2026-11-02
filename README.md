<!doctype html>
<html lang="it">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover">
<title>DI TUTTO UN PO - Mercatino - Solo EURO - WhatsApp 3333661305</title>
<meta name="description" content="DI TUTTO UN PO - Vendita articoli usati - WhatsApp solo messaggi 3333661305 - Solo EURO">
<style>
*{box-sizing:border-box}body{margin:0;font-family:system-ui,Arial;background:#0f1115;color:#e5e7eb;padding:0}
header{position:sticky;top:0;z-index:10;background:#0f1115ee;backdrop-filter:blur(10px);border-bottom:2px solid #facc15;padding:12px;text-align:center}
h1{margin:0;color:#facc15;font-size:22px}h1 span{color:#8b5cf6}
.sub{color:#22c55e;font-size:12px;margin-top:4px;font-weight:800}
.searchBar{display:flex;gap:8px;margin-top:10px;max-width:800px;margin-left:auto;margin-right:auto}
.searchBar input{flex:1;background:#1a1d27;border:1px solid #333;color:#fff;border-radius:10px;padding:12px;font-size:16px}
.searchBar button{background:#facc15;color:#000;border:0;border-radius:10px;padding:12px 16px;font-weight:900;cursor:pointer}
.cats{display:flex;gap:6px;overflow:auto;padding:10px;max-width:1000px;margin:0 auto}
.cat{flex:0 0 auto;background:#1e222e;border:1px solid #333;color:#fff;border-radius:20px;padding:8px 14px;font-size:12px;font-weight:800;cursor:pointer;white-space:nowrap}
.cat.a{background:#facc15;color:#000;border-color:#facc15}
.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(170px,1fr));gap:10px;padding:10px;max-width:1000px;margin:0 auto}
.card{background:#1a1d27;border:1px solid #2a2d3a;border-radius:16px;overflow:hidden;display:flex;flex-direction:column}
.card img{width:100%;height:180px;object-fit:cover;background:#111}
.cardBody{padding:10px;flex:1;display:flex;flex-direction:column}
.cardTitle{font-weight:900;font-size:14px;line-height:1.2;height:36px;overflow:hidden}
.cardPrice{color:#facc15;font-weight:900;font-size:18px;margin-top:6px}
.cardDesc{color:#9aa3b2;font-size:11px;margin-top:4px;height:32px;overflow:hidden}
.cardCat{font-size:10px;color:#8b5cf6;margin-top:4px;font-weight:800}
.cardBtns{display:flex;gap:6px;margin-top:8px}
.btnWa{flex:1;background:#22c55e;color:#000;border:0;border-radius:10px;padding:10px;font-weight:900;font-size:12px;cursor:pointer;text-align:center;text-decoration:none}
.btnInfo{flex:1;background:#1e222e;border:1px solid #333;color:#fff;border-radius:10px;padding:10px;font-weight:800;font-size:11px;cursor:pointer}
footer{text-align:center;padding:20px;color:#777;font-size:11px}
.badgeNew{background:#facc15;color:#000;border-radius:20px;padding:2px 6px;font-size:10px;font-weight:900}
#count{color:#8b5cf6;font-weight:900;font-size:12px;text-align:center;padding:6px}
.modal{position:fixed;inset:0;background:#000c;z-index:99;display:none;align-items:center;justify-content:center;padding:16px}
.modal.on{display:flex}.modalBox{background:#1e222e;border:2px solid #facc15;border-radius:16px;padding:16px;width:100%;max-width:500px;max-height:90vh;overflow:auto}
.modalBox img{width:100%;border-radius:12px}
.thumbs{display:flex;gap:6px;overflow:auto;margin-top:8px}
.thumbs img{width:60px;height:60px;object-fit:cover;border-radius:8px;cursor:pointer;border:2px solid transparent}
.thumbs img.sel{border-color:#facc15}
</style>
</head>
<body>
<header>
<h1>DI TUTTO UN PO <span>🟣</span></h1>
<div class="sub">WhatsApp SOLO MESSAGGI 3333661305 - SOLO EURO - Tavazzano (LO) - Ritiro o spedizione</div>
<div class="searchBar">
<input id="q" placeholder="Cerca: es. ghirlanda, renna, ceramica, lego..." oninput="render()">
<button onclick="render()">CERCA</button>
</div>
<div id="count">Caricamento...</div>
</header>

<div class="cats" id="cats"></div>
<div class="grid" id="grid"></div>

<footer>
DI TUTTO UN PO - WhatsApp 3333661305 solo messaggi - Solo EURO<br>
Tutti gli articoli sono usati salvo indicato - Foto reali - Prezzi in EURO<br>
Per info scrivi su WhatsApp con nome articolo e scatola<br>
<a href="https://wa.me/393333661305" style="color:#22c55e">wa.me/393333661305</a>
</footer>

<div id="modal" class="modal" onclick="if(event.target==this) closeModal()"><div class="modalBox"><div id="modalContent"></div><button class="btnInfo" style="width:100%;margin-top:10px" onclick="closeModal()">CHIUDI</button></div></div>

<script>
let DATA=[];
let FILTER_CAT='Tutte';
const WHATSAPP='393333661305';
const CAT_RULES={"Elettronica":["playstation","xbox","nintendo","console","telefono","iphone","samsung","pc","computer","tablet","cuffie"],"Casa e Cucina":["pentola","padella","piatto","bicchiere","tovaglia","lampada","mobili","sedia","tavolo","cucina"],"Giocattoli e Lego":["lego","gioco","giocattolo","puzzle","bambola","macchinina","hot wheels"],"Collezionismo":["collezione","figura","funko","card","pokemon","manga","fumetto","star wars","marvel"],"Abbigliamento":["maglia","pantalone","scarpa","giacca","cappello","zaino","borsa"],"Libri e Film":["libro","dvd","bluray","film","cd","vinile"],"Natale":["natale","ghirlanda","vimini","renna","babbo natale","stivaletto","ceramica","addobbo","albero","decorazione","natalizia"],"Altro":[]};

function detectCat(o){
 if(o.cat && o.cat!='AUTO') return o.cat;
 let t=(o.n+' '+(o.de||'')).toLowerCase();
 for(let cat in CAT_RULES){ for(let kw of CAT_RULES[cat]) if(t.includes(kw)) return cat; }
 return "Altro";
}

async function loadData(){
 try{
  // 1. Prova a caricare da negozio_data.json (file che carichi su GitHub)
  let res=await fetch('negozio_data.json?v='+Date.now());
  if(res.ok){
   let j=await res.json();
   if(Array.isArray(j) && j.length>0){ DATA=j; renderCats(); render(); return; }
  }
 }catch(e){}
 try{
  // 2. Fallback da localStorage (se apri shop da stessa app)
  let ls=localStorage.getItem('SHOP_AUTO');
  if(ls){ let j=JSON.parse(ls); if(Array.isArray(j) && j.length>0){ DATA=j; renderCats(); render(); return; } }
 }catch(e){}
 document.getElementById('count').textContent='Nessun articolo - Carica negozio_data.json';
 document.getElementById('grid').innerHTML='<p style="grid-column:1/-1;text-align:center;padding:30px;color:#777">Nessun articolo nel negozio.<br>1. Vai nella APP L\'APP - TINO<br>2. Clicca 🟣 PUBBLICA NEGOZIO<br>3. Scarica negozio_data.json<br>4. Caricalo qui su GitHub insieme a questo index.html</p>';
}

function renderCats(){
 let cats=['Tutte',...new Set(DATA.map(detectCat))].sort();
 document.getElementById('cats').innerHTML=cats.map(c=>`<div class="cat ${c===FILTER_CAT?'a':''}" onclick="setCat('${c}')">${c} (${c==='Tutte'?DATA.length:DATA.filter(x=>detectCat(x)===c).length})</div>`).join('');
}

function setCat(c){ FILTER_CAT=c; renderCats(); render(); window.scrollTo(0,0); }

function render(){
 let qv=document.getElementById('q').value.toLowerCase().trim();
 let filtered=DATA.filter(o=>{
  if(FILTER_CAT!=='Tutte' && detectCat(o)!==FILTER_CAT) return false;
  if(qv){
   let t=(o.n+' '+(o.de||'')+' '+(o.sc||'')+' '+(o.prc||'')+' '+detectCat(o)).toLowerCase();
   if(!t.includes(qv)) return false;
  }
  return true;
 });
 // Ordina per ID decrescente = ultimi inseriti prima
 filtered.sort((a,b)=>b.id-a.id);
 document.getElementById('count').textContent=`${filtered.length} articoli in EURO - ${FILTER_CAT} ${qv?' - Ricerca: '+qv:''}`;
 document.getElementById('grid').innerHTML=filtered.map(o=>{
  let cat=detectCat(o);
  let img=(o.im&&o.im[0])?o.im[0]:'https://via.placeholder.com/300?text=No+Foto';
  let price=(o.prc||'').toString().replace(' ,00 Euro','').replace('Euro','').trim()||'';
  if(!price) price=(o.soldPrice||'')+'';
  let waText=encodeURIComponent(`Ciao, sono interessato a: ${o.n} - Prezzo: €${price} - Scatola ${o.sc} Pos ${o.po} - DI TUTTO UN PO - Visto sul negozio GitHub`);
  return `<div class="card">
   <img src="${img}" onclick="openModal(${o.id})" loading="lazy">
   <div class="cardBody">
    <div class="cardTitle">${o.n}</div>
    <div class="cardCat">${cat} ${o.sc!=='SFUSO'?'• Scatola '+o.sc:''}</div>
    <div class="cardPrice">€${price},00</div>
    <div class="cardDesc">${(o.de||'').substring(0,80)}</div>
    <div class="cardBtns">
     <a class="btnWa" href="https://wa.me/${WHATSAPP}?text=${waText}" target="_blank">💬 WhatsApp</a>
     <button class="btnInfo" onclick="openModal(${o.id})">Vedi</button>
    </div>
   </div>
  </div>`;
 }).join('') || '<p style="grid-column:1/-1;text-align:center;padding:30px;color:#777">Nessun articolo trovato con questi filtri</p>';
}

function openModal(id){
 let o=DATA.find(x=>x.id===id); if(!o) return;
 let cat=detectCat(o);
 let price=(o.prc||'').toString().replace(' ,00 Euro','').replace('Euro','').trim()||o.soldPrice||'';
 let waText=encodeURIComponent(`Ciao DI TUTTO UN PO, voglio info su:\n${o.n}\nPrezzo: €${price}\nScatola ${o.sc} Pos ${o.po}\nCategoria: ${cat}\nVisto su negozio GitHub - Tavazzano`);
 let imgs=(o.im||[]).map((src,i)=>`<img src="${src}" class="${i===0?'sel':''}" onclick="document.getElementById('mainImg').src=this.src;document.querySelectorAll('.thumbs img').forEach(im=>im.classList.remove('sel'));this.classList.add('sel')">`).join('');
 document.getElementById('modalContent').innerHTML=`
  <img id="mainImg" src="${(o.im&&o.im[0])?o.im[0]:''}">
  <div class="thumbs">${imgs}</div>
  <h2 style="margin:10px 0 0 0;color:#facc15">${o.n}</h2>
  <div style="color:#8b5cf6;font-weight:900;font-size:12px">${cat} ${o.sc!=='SFUSO'?'- Scatola '+o.sc+' Pos '+o.po:''}</div>
  <div style="color:#facc15;font-weight:900;font-size:26px;margin-top:8px">€${price},00</div>
  <div style="color:#22c55e;font-size:11px;font-weight:800">WhatsApp solo messaggi 3333661305 - Solo EURO</div>
  <p style="color:#e5e7eb;font-size:13px;white-space:pre-wrap;margin-top:10px">${o.de||'Nessuna descrizione - Chiedi info su WhatsApp'}</p>
  <div style="margin-top:12px;background:#0f1115;padding:8px;border-radius:8px;font-size:11px">
  <b>Quotazione EURO:</b><br>
  NUOVO simile: €22-36 ghirlande con peluche<br>
  USATO: €12-20 su Subito/Vinted/Wallapop<br>
  Prezzo DI TUTTO UN PO: €${price},00
  </div>
  <a href="https://wa.me/${WHATSAPP}?text=${waText}" target="_blank" style="display:block;background:#22c55e;color:#000;text-align:center;padding:14px;border-radius:12px;font-weight:900;text-decoration:none;margin-top:12px">💬 CONTATTA SU WHATSAPP - 3333661305</a>
  <p style="font-size:10px;color:#777;text-align:center;margin-top:8px">Ritiro a Tavazzano (LO) o spedizione - Solo EURO</p>
 `;
 document.getElementById('modal').classList.add('on');
}
function closeModal(){ document.getElementById('modal').classList.remove('on'); }

loadData();
</script>
</body>
</html>
