<script>
(function(){
"use strict";
const MATH_AUTRES={
 "Arithmétique":["Les nombres","Addition","Soustraction","Multiplication","Division","Fractions","Problèmes"],
 "Géométrie":["Droites et angles","Figures planes","Solides","Périmètre et aire"],
 "Mesures":["Longueurs","Masses","Capacités","Durées","Monnaie"]
};
const FIELDS=["classe","disc","dom","notion","type","duree","ecole","enseignant","date","periode","competence","objectif","prerequis","materiel","situation","observation"];
const KEY="apcBeninForm";
const today=()=>{const d=new Date();return d.getFullYear()+"-"+String(d.getMonth()+1).padStart(2,"0")+"-"+String(d.getDate()).padStart(2,"0");};

window.escapeHTML=function(s){
 return String(s??"").replace(/\u00ad/g,"").replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
};
window.section=function(title,content){
 let c=content||"À compléter selon la séance.";
 if(/^1\. Proposer une tâche simple/.test(c))
  c="Exercice 1 (reconnaissance) : [à compléter]\nExercice 2 (application) : [à compléter], adapté au niveau de la classe.\nExercice 3 (réinvestissement) : [à compléter], situation nouvelle ou court problème.";
 const t=escapeHTML(c).replace(/__EXERCISE_NL__|\n/g,"<br>");
 return `<section class="fiche-section"><h3>${title}</h3><p>${t}</p></section>`;
};
window.populateNotions=function(){
 const disc=$("disc").value,domain=$("dom").value,classe=$("classe").value,s=$("notion"),old=s.value;
 s.innerHTML="";
 let items=(D[disc]&&D[disc][domain])?D[disc][domain]:[];
 if(classe==="CI"&&disc==="Français"&&domain==="Lecture et sons")items=Object.keys(FR_CI);
 if(disc==="Mathématiques"&&classe!=="CI")items=MATH_AUTRES[domain]||[];
 items.forEach(x=>s.add(new Option(x,x)));
 if([...s.options].some(x=>x.value===old))s.value=old;
 updateSourceNotice();
};
const g0=window.generate;
window.generate=function(){
 const d=$("duree");d.value=Math.min(180,Math.max(10,Number(d.value)||30));
 g0();
 const t=$("type").value;
 if(t!=="fiche"&&t!=="pack"){const tb=$("fiche").querySelector("table");if(tb)tb.closest(".fiche-section").remove();}
 saveForm();
};
function saveForm(){
 try{const o={};FIELDS.forEach(k=>o[k]=$(k).value);localStorage.setItem(KEY,JSON.stringify(o));}catch(e){}
}
function setVal(k,v){
 const e=$(k);if(v===undefined||v===null)return;
 if(e.tagName==="SELECT"&&![...e.options].some(o=>o.value===v))return;
 e.value=v;
}
function loadForm(){
 try{
  const o=JSON.parse(localStorage.getItem(KEY)||"null");if(!o)return;
  setVal("classe",o.classe);setVal("disc",o.disc);populateDomains();
  setVal("dom",o.dom);populateNotions();setVal("notion",o.notion);
  FIELDS.slice(4).forEach(k=>setVal(k,o[k]));
 }catch(e){}
}
window.resetForm=function(){
 try{localStorage.removeItem(KEY);}catch(e){}
 ["ecole","enseignant","periode","competence","objectif","prerequis","materiel","situation","observation"].forEach(k=>$(k).value="");
 $("date").value=today();$("duree").value=30;$("type").value="fiche";
 $("classe").value="CI";$("disc").value="Français";populateDomains();
 $("fiche").innerHTML='<p class="empty">Votre fiche pédagogique apparaîtra ici après avoir appuyé sur « Générer la fiche ».</p>';
};
function downloadWord(){
 const el=$("fiche");
 if(el.querySelector(".empty")){alert("Générez d'abord une fiche.");return;}
 const css="body{font-family:Arial,sans-serif;font-size:11pt}table{border-collapse:collapse;width:100%}th,td{border:1px solid #777;padding:4px;vertical-align:top;font-size:9pt}th{background:#edf5ef}h2,h3{color:#185d39}.warning{border-left:4px solid #d5a53b;padding:4px}.info{border:1px solid #ccc;padding:5px;margin:3px 0}.meta div{display:inline-block;width:32%}";
 const html='<html xmlns:o="urn:schemas-microsoft-com:office:office" xmlns:w="urn:schemas-microsoft-com:office:word"><head><meta charset="utf-8"><style>'+css+'</style></head><body>'+el.innerHTML+'</body></html>';
 const a=document.createElement("a");
 a.href=URL.createObjectURL(new Blob(["\ufeff",html],{type:"application/msword"}));
 a.download="fiche-pedagogique.doc";document.body.appendChild(a);a.click();a.remove();
 setTimeout(()=>URL.revokeObjectURL(a.href),1000);
}
const w=document.createElement("button");
w.className="secondary";w.id="word";w.textContent="Télécharger (Word)";
$("print").before(w);
["disc","dom","classe","generate","copy","print","reset"].forEach(id=>{const e=$(id);e.replaceWith(e.cloneNode(true));});
$("disc").addEventListener("change",()=>populateDomains());
$("dom").addEventListener("change",()=>populateNotions());
$("classe").addEventListener("change",()=>populateDomains());
$("generate").addEventListener("click",()=>generate());
$("copy").addEventListener("click",()=>copyDocument());
$("print").addEventListener("click",()=>window.print());
$("reset").addEventListener("click",()=>resetForm());
$("word").addEventListener("click",downloadWord);
const fp=document.querySelector(".form-panel");
fp.addEventListener("input",saveForm);fp.addEventListener("change",saveForm);
populateDomains();loadForm();
if(!$("date").value)$("date").value=today();
})();
</script>