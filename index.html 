
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Bot pédagogique APC Bénin</title>
<style>
:root{--vert:#176534;--fond:#f0f5f1;--texte:#183323}
*{box-sizing:border-box}
body{margin:0;background:var(--fond);color:var(--texte);font-family:Arial,sans-serif;line-height:1.5}
header{background:var(--vert);color:white;text-align:center;padding:22px 12px}
header h1{margin:0;font-size:24px}
main{max-width:1000px;margin:20px auto;padding:0 12px}
.card{background:white;border-radius:10px;padding:18px;margin-bottom:18px;box-shadow:0 2px 8px #0001}
h2,h3{color:var(--vert)}
h2{font-size:21px;margin-top:0}
h3{font-size:17px;margin-bottom:8px}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:12px}
.field{margin-bottom:12px}
label{display:block;font-weight:bold;margin-bottom:4px}
input,select,textarea{width:100%;padding:10px;border:1px solid #b7c8bb;border-radius:6px;font:inherit;background:white}
textarea{min-height:75px;resize:vertical}
button{border:0;border-radius:6px;padding:12px 16px;background:var(--vert);color:white;font-weight:bold;font-size:15px;cursor:pointer;margin:5px 4px 5px 0}
.secondary{background:#52665a}
.small{font-size:13px;color:#52665a}
#fiche{display:none}
.meta{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:5px 15px}
.meta p{margin:4px 0}
table{width:100%;border-collapse:collapse;background:white}
th,td{border:1px solid #65756a;padding:7px;vertical-align:top;text-align:left}
th{background:#e2eee5}
.notes{margin-top:18px;border:1px solid #777;padding:10px;min-height:70px}
@media(max-width:650px){table{font-size:11px}th,td{padding:4px}}
@media print{
body{background:white;color:black;font-size:10pt}
header{background:white;color:black;padding:4px}
main{margin:0;padding:0;max-width:none}
#formulaire,.no-print{display:none!important}
#fiche{display:block!important}
.card{box-shadow:none;padding:0;margin:0}
table{font-size:8pt}
th,td{padding:4px}
tr{page-break-inside:avoid}
@page{size:A4 landscape;margin:9mm}
}
</style>
</head>
<body>
<header>
<h1>Bot pédagogique APC Bénin</h1>
<p>Préparation de leçons et résumés de cours — CI à CM2</p>
</header>

<main>
<section id="formulaire" class="card">
<h2>Préparer un document pédagogique</h2>
<p class="small">Complète les informations utiles. Les propositions automatiques doivent être adaptées à la notion et au programme de la classe.</p>

<form id="form">
<h3>1. Informations générales</h3>
<div class="grid">
<div class="field"><label for="ecole">École</label><input id="ecole"></div>
<div class="field"><label for="enseignant">Enseignant(e)</label><input id="enseignant"></div>
<div class="field"><label for="classe">Classe *</label>
<select id="classe" required><option value="">Choisir</option><option>CI</option><option>CP</option><option>CE1</option><option>CE2</option><option>CM1</option><option>CM2</option></select></div>
<div class="field"><label for="discipline">Discipline *</label>
<select id="discipline" required><option value="">Choisir</option><option>Français</option><option>Mathématiques</option><option>Éducation sociale</option><option>EST</option><option>Éducation artistique</option><option>EPS</option></select></div>
<div class="field"><label for="domaine">Sous-discipline / domaine</label><input id="domaine" placeholder="Ex. : Arithmétique, Histoire, Chant"></div>
<div class="field"><label for="typeDoc">Type de document *</label>
<select id="typeDoc"><option>Fiche de préparation complète</option><option>Résumé de cours</option></select></div>
<div class="field"><label for="theme">Thème</label><input id="theme"></div>
<div class="field"><label for="sa">Situation d’apprentissage</label><textarea id="sa"></textarea></div>
<div class="field"><label for="seance">Situation / séance n°</label><input id="seance" placeholder="Ex. : SA 1, séance 2"></div>
<div class="field"><label for="date">Date</label><input id="date" type="date"></div>
<div class="field"><label for="duree">Durée en minutes *</label><input id="duree" type="number" min="5" max="180" value="30" required></div>
<div class="field"><label for="notion">Titre de la leçon *</label><input id="notion" required placeholder="Ex. : Les diphtongues"></div>
</div>

<h3>2. Compétences et préparation</h3>
<div class="field"><label for="competence">Compétence disciplinaire</label><textarea id="competence"></textarea></div>
<div class="field"><label for="transversales">Compétences transversales / CTD</label><textarea id="transversales"></textarea></div>
<div class="field"><label for="connaissances">Connaissances et techniques</label><textarea id="connaissances"></textarea></div>
<div class="field"><label for="strategies">Stratégies d’enseignement, d’apprentissage et d’évaluation</label><textarea id="strategies" placeholder="Travail individuel, en groupe, collectif, observation..."></textarea></div>
<div class="field"><label for="materiel">Matériel et supports</label><textarea id="materiel"></textarea></div>
<div class="field"><label for="prerequis">Prérequis / acquis antérieurs</label><textarea id="prerequis"></textarea></div>
<div class="field"><label for="objectif">Objectif spécifique / résultat d’apprentissage visé</label><textarea id="objectif" placeholder="À la fin de la séance, l’apprenant sera capable de..."></textarea></div>

<h3>3. Déroulement pédagogique</h3>
<div class="field"><label for="rappel">Rappel</label><textarea id="rappel"></textarea></div>
<div class="field"><label for="mise">Mise en situation / situation de départ</label><textarea id="mise"></textarea></div>
<div class="field"><label for="acquis">Émergence des acquis antérieurs</label><textarea id="acquis"></textarea></div>
<div class="field"><label for="nouveau">Proposition de nouvelles acquisitions</label><textarea id="nouveau"></textarea></div>
<div class="field"><label for="realisation">Réalisation / construction des nouveaux savoirs</label><textarea id="realisation"></textarea></div>
<div class="field"><label for="synthese">Synthèse / trace écrite</label><textarea id="synthese"></textarea></div>
<div class="field"><label for="application">Application / exercices</label><textarea id="application"></textarea></div>
<div class="field"><label for="objectivation">Objectivation</label><textarea id="objectivation"></textarea></div>
<div class="field"><label for="evaluation">Évaluation orale ou écrite</label><textarea id="evaluation"></textarea></div>
<div class="field"><label for="projection">Projection / réinvestissement</label><textarea id="projection"></textarea></div>
<div class="field"><label for="remediation">Remédiation prévue</label><textarea id="remediation"></textarea></div>
<div class="field"><label for="notes">Notes personnelles / observations</label><textarea id="notes"></textarea></div>

<div class="actions">
<button type="submit">Générer le document</button>
<button type="button" class="secondary" id="effacer">Effacer le formulaire</button>
</div>
</form>
</section>

<section id="fiche" class="card">
<div class="actions no-print">
<button type="button" onclick="window.print()">Imprimer / Enregistrer en PDF</button>
<button type="button" class="secondary" onclick="retour()">Modifier le formulaire</button>
</div>
<div id="sortie"></div>
</section>
</main>

<script>
const $=id=>document.getElementById(id);
const ids=["ecole","enseignant","classe","discipline","domaine","typeDoc","theme","sa","seance","date","duree","notion","competence","transversales","connaissances","strategies","materiel","prerequis","objectif","rappel","mise","acquis","nouveau","realisation","synthese","application","objectivation","evaluation","projection","remediation","notes"];

function v(id){return $(id).value.trim()}
function esc(s){return String(s||"").replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]))}
function val(id,def="À compléter"){return esc(v(id)||def)}
function p(label,id,def="À compléter"){return `<p><strong>${label} :</strong> ${val(id,def)}</p>`}
function suggestions(){
 const n=v("notion"),c=v("classe"),d=v("discipline");
 const sujet=`la notion « ${n} » en ${d}, classe ${c}`;
 return {
 rappel:`Faire rappeler une connaissance antérieure utile pour étudier ${n}.`,
 mise:`Présenter une situation concrète adaptée à ${sujet}, puis poser une question qui suscite la recherche.`,
 acquis:`Questionner les apprenants sur ce qu’ils savent déjà et recueillir leurs réponses.`,
 nouveau:`Annoncer la nouvelle acquisition : étudier ${n}. Faire exprimer aux apprenants ce qu’ils pensent découvrir.`,
 realisation:`Guider l’observation, la recherche, la manipulation ou l’analyse. Faire proposer, comparer et justifier les réponses liées à ${n}.`,
 synthese:`Faire formuler l’essentiel de la leçon. Compléter avec la définition, la règle ou la méthode exacte validée par l’enseignant.`,
 application:`Proposer des exercices progressifs sur ${n}, adaptés au niveau ${c}.`,
 objectivation:`Demander aux apprenants ce qu’ils ont appris, comment ils l’ont appris et les difficultés rencontrées.`,
 evaluation:`Proposer une tâche individuelle permettant de vérifier l’objectif d’apprentissage sur ${n}.`,
 projection:`Demander aux apprenants comment ils pourront réutiliser cet apprentissage dans une nouvelle situation.`,
 remediation:`Reprendre la notion avec des exemples plus simples et un accompagnement ciblé pour les apprenants en difficulté.`
 };
}
function row(t,d,c,r,e){
 return `<tr><td><strong>${t}</strong><br>${d} min</td><td>${esc(c)}</td><td>${esc(r)}</td><td>${esc(e)}</td></tr>`;
}
function durees(total){
 const parts=[10,10,10,5,35,10,10,10];
 let a=parts.map(x=>Math.floor(total*x/100));
 let reste=total-a.reduce((s,x)=>s+x,0);
 for(let i=0;i<reste;i++)a[i%a.length]++;
 return a;
}
function generer(e){
 e.preventDefault();
 const total=Math.max(5,Number(v("duree"))||30);
 const s=suggestions();
 const titre=v("typeDoc");
 let html=`<h2>${val("notion")} — ${val("discipline")}</h2>
 <div class="meta">
 ${p("École","ecole")}${p("Enseignant(e)","enseignant")}
 ${p("Classe","classe")}${p("Discipline","discipline")}
 ${p("Sous-discipline / domaine","domaine")}${p("Thème","theme")}
 ${p("Situation d’apprentissage","sa")}${p("Situation / séance n°","seance")}
 ${p("Date","date")}${p("Durée","duree")} min
 </div><hr>
 ${p("Compétence disciplinaire","competence")}
 ${p("Compétences transversales / CTD","transversales")}
 ${p("Connaissances et techniques","connaissances")}
 ${p("Stratégies d’enseignement, d’apprentissage et d’évaluation","strategies")}
 ${p("Matériel","materiel")}
 ${p("Prérequis","prerequis")}
 ${p("Objectif spécifique","objectif")}`;
 if(titre==="Résumé de cours"){
 html+=`<h3>Résumé de cours : ${val("notion")}</h3>
 ${p("Notion / leçon à retenir","synthese","À rédiger et vérifier selon le cours étudié.")}
 ${p("Exercices d’application","application")}
 ${p("Évaluation","evaluation")}
 ${p("Remédiation","remediation")}
 ${p("Réinvestissement","projection")}`;
 }else{
 const d=durees(total);
 html+=`<h3>Déroulement</h3>
 <table><thead><tr><th>Étapes / durée</th><th>CONSIGNES de l’enseignant</th><th>Activités des apprenants</th><th>RÉSULTATS ATTENDUS / observations</th></tr></thead><tbody>`;
 html+=row("Rappel",d[0],v("rappel")||s.rappel,"Réactivent leurs acquis antérieurs.","Les connaissances utiles sont rappelées.");
 html+=row("INTRODUCTION — Mise en situation",d[1],v("mise")||s.mise,"Écoutent, observent et réagissent.","La situation de départ est comprise.");
 html+=row("Émergence des acquis antérieurs",d[2],v("acquis")||s.acquis,"Expriment leurs connaissances et répondent aux questions.","Les acquis et les besoins sont identifiés.");
 html+=row("Proposition de nouvelles acquisitions",d[3],v("nouveau")||s.nouveau,"Identifient la nouvelle notion à étudier.","L’objectif de la séance est compris.");
 html+=row("RÉALISATION — Construction des savoirs",d[4],v("realisation")||s.realisation,"Recherchent, observent, manipulent, proposent et justifient leurs réponses.","Les notions visées sont construites progressivement.");
 html+=row("Synthèse / application",d[5],v("synthese")||s.synthese,"Formulent l’essentiel puis réalisent les exercices proposés : "+(v("application")||s.application),"La règle ou la méthode est formulée et mise en pratique.");
 html+=row("RETOUR ET PROJECTION — Objectivation",d[6],v("objectivation")||s.objectivation,"Expliquent ce qu’ils ont appris et les difficultés rencontrées.","Les apprentissages sont explicités.");
 html+=row("Évaluation / projection",d[7],(v("evaluation")||s.evaluation)+" Projection : "+(v("projection")||s.projection),"Réalisent la tâche d’évaluation et proposent un réinvestissement.","Le degré d’atteinte de l’objectif est observé.");
 html+=`</tbody></table>
 <h3>Trace écrite / synthèse</h3><p style="white-space:pre-wrap">${val("synthese","À compléter avec la trace écrite exacte du cours.")}</p>
 <h3>Remédiation</h3><p>${val("remediation",s.remediation)}</p>
 <h3>Notes personnelles</h3><div class="notes">${val("notes","Durée réelle : ____________________<br>Problèmes rencontrés : ____________________<br>Suggestions : ____________________")}</div>`;
 }
 html+=`<p class="small">Document généré automatiquement à partir des informations saisies. Vérifier l’exactitude des compétences, des contenus, des consignes, des résultats attendus et des durées selon les programmes et guides officiels applicables au Bénin.</p>`;
 $("sortie").innerHTML=html;
 $("formulaire").style.display="none";
 $("fiche").style.display="block";
 window.scrollTo(0,0);
}
function retour(){
 $("fiche").style.display="none";
 $("formulaire").style.display="block";
 window.scrollTo(0,0);
}
$("form").addEventListener("submit",generer);
$("effacer").addEventListener("click",()=>{
 if(confirm("Effacer toutes les informations saisies ?"))$("form").reset();
});
</script>
</body>
</html>
