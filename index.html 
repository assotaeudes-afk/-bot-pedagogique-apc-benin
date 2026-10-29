
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#185d39">
<title>Bot pédagogique APC Bénin</title>
<style>
:root{--vert:#185d39;--vert2:#28784c;--clair:#eef7f0;--or:#e5b84b;--texte:#202820;--gris:#657067;--bord:#d7e1d9;--fond:#f5f8f5}
*{box-sizing:border-box}
body{margin:0;background:var(--fond);color:var(--texte);font-family:Arial,Helvetica,sans-serif;line-height:1.45}
header{background:linear-gradient(120deg,var(--vert),var(--vert2));color:#fff;padding:24px 16px;text-align:center}
header h1{margin:0 0 5px;font-size:clamp(1.5rem,4vw,2.2rem)}
header p{margin:0}
main{max-width:1100px;margin:20px auto;padding:0 12px 35px}
.panel{background:#fff;border:1px solid var(--bord);border-radius:14px;padding:18px;margin-bottom:18px;box-shadow:0 3px 12px #183c2410}
h2{font-size:1.2rem;color:var(--vert);margin:0 0 14px}
h3{color:var(--vert);margin:18px 0 8px}
.grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:12px}
.field{display:flex;flex-direction:column;gap:5px}
.field.full{grid-column:1/-1}
label{font-weight:700;font-size:.92rem}
input,select,textarea{font:inherit;width:100%;padding:10px;border:1px solid #bdcabe;border-radius:8px;background:#fff;color:var(--texte)}
textarea{min-height:78px;resize:vertical}
.buttons{display:flex;flex-wrap:wrap;gap:9px;margin-top:15px}
button{border:0;border-radius:9px;padding:11px 15px;font:inherit;font-weight:700;cursor:pointer}
.primary{background:var(--vert);color:white}
.secondary{background:#e8f1ea;color:var(--vert)}
.danger{background:#fff0ee;color:#8a2d22}
.small{font-size:.86rem;color:var(--gris)}
.notice{padding:11px 13px;background:#fff8e5;border-left:4px solid var(--or);border-radius:6px;font-size:.9rem}
#fiche{background:white;border:1px solid var(--bord);border-radius:12px;padding:22px;min-height:120px}
.empty{color:var(--gris);text-align:center;padding:30px 8px}
.fiche-head{text-align:center;border-bottom:2px solid var(--vert);padding-bottom:12px;margin-bottom:14px}
.fiche-head h2{margin:0;font-size:1.4rem;text-transform:uppercase}
.fiche-head h3{margin:6px 0;color:var(--texte);font-size:1.1rem}
.fiche-head p{margin:3px}
.meta{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:7px 14px;margin:12px 0}
.meta div{border-bottom:1px dotted #aab8ad;padding:4px 0}
.fiche-section{margin-top:16px;break-inside:avoid}
.fiche-section h3{font-size:1rem;background:var(--clair);padding:7px 9px;border-left:4px solid var(--vert);margin:0 0 8px}
.fiche-section p{margin:6px 0;white-space:pre-wrap}
table{width:100%;border-collapse:collapse;font-size:.88rem;margin-top:8px}
th,td{border:1px solid #9eafa2;padding:8px;text-align:left;vertical-align:top;white-space:pre-wrap}
th{background:#edf5ef;color:#163d27}
footer{text-align:center;color:var(--gris);padding:12px;font-size:.85rem}
@media(max-width:650px){.grid,.meta{grid-template-columns:1fr}.panel{padding:13px}#fiche{padding:13px}table{font-size:.78rem}th,td{padding:5px}}
@page{size:A4;margin:13mm}
@media print{
body{background:#fff;font-size:10pt}
header,.formulaire,.actions,footer,.notice,.no-print{display:none!important}
main{max-width:none;margin:0;padding:0}
.panel{border:0;box-shadow:none;padding:0;margin:0}
#fiche{border:0;border-radius:0;padding:0;min-height:0}
.fiche-head h2{font-size:16pt}
.fiche-head h3{font-size:12pt}
table{font-size:8.5pt;page-break-inside:auto}
tr{page-break-inside:avoid}
th,td{padding:5px}
.fiche-section{break-inside:avoid}
}
</style>
</head>
<body>
<header>
<h1>Bot pédagogique APC Bénin</h1>
<p>Préparation des fiches pédagogiques du primaire — CI à CM2</p>
</header>
<main>
<section class="panel formulaire">
<h2>1. Informations de la fiche</h2>
<div class="grid">
<div class="field"><label for="classe">Classe *</label><select id="classe"><option>CI</option><option>CP</option><option>CE1</option><option>CE2</option><option>CM1</option><option>CM2</option></select></div>
<div class="field"><label for="discipline">Discipline *</label><select id="discipline"></select></div>
<div class="field"><label for="notionCatalogue">Notion du catalogue</label><select id="notionCatalogue"><option value="">— Choisir une notion —</option></select></div>
<div class="field"><label for="titre">Titre de la leçon *</label><input id="titre" placeholder="Ex. Les nombres de 0 à 99"></div>
<div class="field"><label for="domaine">Domaine / sous-domaine</label><input id="domaine" placeholder="Ex. Arithmétique, vocabulaire..."></div>
<div class="field"><label for="duree">Durée</label><input id="duree" value="45 min"></div>
<div class="field"><label for="unite">Unité / période</label><input id="unite" placeholder="Unité, trimestre ou période"></div>
<div class="field"><label for="sa">Situation d’apprentissage (SA)</label><input id="sa" placeholder="Numéro ou intitulé"></div>
<div class="field"><label for="sequence">Séquence / séance</label><input id="sequence" placeholder="Ex. Séquence 1, séance 2"></div>
<div class="field"><label for="numero">Numéro de fiche</label><input id="numero" placeholder="Facultatif"></div>
<div class="field"><label for="date">Date de déroulement</label><input id="date" type="date"></div>
<div class="field"><label for="ecole">École</label><input id="ecole" placeholder="Nom de l’école"></div>
<div class="field"><label for="enseignant">Enseignant(e)</label><input id="enseignant" placeholder="Nom de l’enseignant(e)"></div>
<div class="field"><label for="effectif">Effectif de la classe</label><input id="effectif" type="number" min="0" placeholder="Nombre d’élèves"></div>
<div class="field full"><label for="competence">Compétence disciplinaire</label><textarea id="competence" placeholder="Compétence visée"></textarea></div>
<div class="field full"><label for="competencesTrans">Compétences transversales / transdisciplinaires</label><textarea id="competencesTrans" placeholder="À préciser selon le guide officiel utilisé"></textarea></div>
<div class="field full"><label for="connaissances">Connaissances et techniques</label><textarea id="connaissances" placeholder="Savoirs et savoir-faire visés"></textarea></div>
<div class="field full"><label for="strategies">Stratégies d’enseignement, d’apprentissage et d’évaluation</label><textarea id="strategies" placeholder="Travail individuel, en groupe, collectif, manipulation..."></textarea></div>
<div class="field full"><label for="materiel">Matériel pédagogique</label><textarea id="materiel" placeholder="Manuels, ardoises, images, objets, matériel sportif..."></textarea></div>
</div>
</section>

<section class="panel formulaire">
<h2>2. Préparation pédagogique</h2>
<div class="grid">
<div class="field full"><label for="prerequis">Prérequis</label><textarea id="prerequis" placeholder="Ce que les élèves doivent déjà savoir ou savoir-faire"></textarea></div>
<div class="field full"><label for="objectif">Objectif(s) d’apprentissage</label><textarea id="objectif" placeholder="À la fin de la séance, l’élève sera capable de..."></textarea></div>
<div class="field full"><label for="situation">Mise en situation / situation-problème</label><textarea id="situation" placeholder="Situation de départ liée à la vie des élèves"></textarea></div>
<div class="field full"><label for="trace">Trace écrite / synthèse attendue</label><textarea id="trace" placeholder="Règle, définition, méthode ou résumé à retenir"></textarea></div>
<div class="field full"><label for="remediation">Remédiation / différenciation</label><textarea id="remediation" placeholder="Aides prévues pour les élèves en difficulté et approfondissement"></textarea></div>
<div class="field full"><label for="projection">Projection / réinvestissement</label><textarea id="projection" placeholder="Comment les élèves réutiliseront-ils les acquis ?"></textarea></div>
</div>
</section>

<section class="panel formulaire">
<h2>3. Déroulement de la séance</h2>
<p class="small">Les phases proposées sont un modèle adaptable. Modifie les consignes, stratégies et résultats attendus selon ta fiche et ta discipline.</p>
<div class="grid">
<div class="field"><label for="phase1">Activités préparatoires / rappel</label><textarea id="phase1">L’enseignant vérifie les prérequis et rappelle les acquis utiles.</textarea></div>
<div class="field"><label for="attendu1">Résultats attendus</label><textarea id="attendu1">Les élèves mobilisent les acquis nécessaires.</textarea></div>
<div class="field"><label for="phase2">Introduction / mise en situation</label><textarea id="phase2">L’enseignant présente la situation-problème et fait émerger les représentations.</textarea></div>
<div class="field"><label for="attendu2">Résultats attendus</label><textarea id="attendu2">Les élèves observent, s’expriment et formulent des questions ou hypothèses.</textarea></div>
<div class="field"><label for="phase3">Réalisation / construction des savoirs</label><textarea id="phase3">Les élèves recherchent, observent, manipulent, échangent et confrontent leurs réponses. L’enseignant guide et valide les acquis.</textarea></div>
<div class="field"><label for="attendu3">Résultats attendus</label><textarea id="attendu3">Les élèves construisent la notion et justifient leurs réponses.</textarea></div>
<div class="field"><label for="phase4">Application / entraînement</label><textarea id="phase4">Les élèves réalisent des exercices ou une tâche adaptée à la notion.</textarea></div>
<div class="field"><label for="attendu4">Résultats attendus</label><textarea id="attendu4">Les élèves appliquent correctement la notion étudiée.</textarea></div>
<div class="field"><label for="phase5">Retour / objectivation</label><textarea id="phase5">L’enseignant invite les élèves à dire ce qu’ils ont appris et les difficultés rencontrées.</textarea></div>
<div class="field"><label for="attendu5">Résultats attendus</label><textarea id="attendu5">Les élèves expliquent l’essentiel de l’apprentissage réalisé.</textarea></div>
<div class="field"><label for="phase6">Évaluation</label><textarea id="phase6">Proposer une tâche courte permettant de vérifier l’atteinte de l’objectif.</textarea></div>
<div class="field"><label for="attendu6">Résultats attendus</label><textarea id="attendu6">Les élèves réalisent correctement la tâche d’évaluation.</textarea></div>
<div class="field full"><label for="consigne">Consigne / exercice d’évaluation</label><textarea id="consigne" placeholder="Écris ici une consigne concrète et observable"></textarea></div>
</div>
<div class="buttons">
<button class="primary" type="button" id="generer">Générer la fiche complète</button>
<button class="secondary" type="button" id="vider">Effacer les champs de préparation</button>
</div>
</section>

<section class="panel">
<h2>4. Fiche générée</h2>
<div class="notice no-print">Vérifie et complète la fiche avant de l’imprimer. Les champs officiels qui ne figurent pas dans tes documents de référence doivent être confirmés à partir du guide APC applicable.</div>
<div id="fiche"><div class="empty">Remplis les informations, puis appuie sur « Générer la fiche complète ».</div></div>
<div class="buttons actions">
<button class="primary" type="button" id="imprimer">Imprimer / Enregistrer en PDF</button>
<button class="secondary" type="button" id="copier">Copier le texte de la fiche</button>
</div>
<p id="message" class="small actions" aria-live="polite"></p>
</section>
</main>
<footer>Bot pédagogique APC Bénin — outil de préparation à vérifier et adapter aux guides officiels en vigueur.</footer>
<!-- COLLE LA PARTIE 2 ICI, À LA PLACE DE CETTE LIGNE -->
</body>
</html>

<script>
const disciplines = [
"Français","Mathématiques — Arithmétique","Mathématiques — Géométrie","Mathématiques — Mesures",
"Éducation sociale — Morale","Éducation sociale — Civisme","Éducation sociale — Histoire-Géographie",
"Éducation sociale — Langues et culture","EST","Éducation artistique — Dessin","Éducation artistique — Chant",
"Éducation artistique — Travaux manuels","Éducation artistique — Poésie","Éducation artistique — Conte",
"Éducation artistique — Couture","EPS"
];

const catalogue = {
"CI":{
"Français":["Langage oral : se présenter","Écoute et compréhension de consignes","Vocabulaire de la classe","Préparation au geste graphique"],
"Mathématiques — Arithmétique":["Tri et classement d’objets","Dénombrement de petites collections","Comparaison de quantités"],
"Mathématiques — Géométrie":["Reconnaissance de formes simples","Repérage dans l’espace"],
"Mathématiques — Mesures":["Comparaison de longueurs","Repérage des moments de la journée"],
"Éducation sociale — Morale":["Politesse et respect des autres"],
"Éducation sociale — Civisme":["Respect du matériel collectif"],
"Éducation sociale — Histoire-Géographie":["La famille et le milieu proche"],
"Éducation sociale — Langues et culture":["Comptines et expressions du milieu"],
"EST":["Hygiène corporelle","Reconnaissance des objets usuels"],
"Éducation artistique — Dessin":["Traces et traits libres"],
"Éducation artistique — Chant":["Chants et comptines enfantines"],
"Éducation artistique — Travaux manuels":["Modelage et assemblage simples"],
"Éducation artistique — Poésie":["Récitation de comptines"],
"Éducation artistique — Conte":["Écoute et compréhension d’un conte"],
"Éducation artistique — Couture":["Découverte des matériaux et gestes simples"],
"EPS":["Marcher, courir et s’arrêter","Équilibre et déplacements simples"]
},
"CP":{
"Français":["Compréhension de consignes simples","Lecture et écriture de syllabes","Copie de mots et de courtes phrases","Vocabulaire du milieu de vie"],
"Mathématiques — Arithmétique":["Nombres de 0 à 99 : comptage, lecture et écriture","Comparer et ranger les nombres de 0 à 99","Addition et soustraction","Le nombre 100 : composition, représentation, identification, lecture et écriture","Résolution de problèmes simples"],
"Mathématiques — Géométrie":["Reconnaître et décrire le cube","Repérage et formes géométriques simples"],
"Mathématiques — Mesures":["Comparer des longueurs","Mesurer avec des unités usuelles de la classe"],
"Éducation sociale — Morale":["Respect, entraide et politesse"],
"Éducation sociale — Civisme":["Règles de vie en classe et à l’école"],
"Éducation sociale — Histoire-Géographie":["La famille et l’école","Se repérer dans le milieu proche"],
"Éducation sociale — Langues et culture":["Expressions et pratiques culturelles du milieu"],
"EST":["Hygiène et santé","Aliments sains et protection des aliments","Utilisation prudente du foyer et du réchaud","Les différents types de marmites"],
"Éducation artistique — Dessin":["Dessiner des objets familiers"],
"Éducation artistique — Chant":["Chants du répertoire enfantin"],
"Éducation artistique — Travaux manuels":["Découpage, pliage et assemblage"],
"Éducation artistique — Poésie":["Récitation d’un poème court"],
"Éducation artistique — Conte":["Écoute et restitution d’un conte"],
"Éducation artistique — Couture":["Initiation aux gestes simples et à la sécurité"],
"EPS":["Actions locomotrices et non locomotrices","Exécution d’actions avec l’ensemble du corps","Saut vers l’avant","Saut vers l’arrière","Saut vers le haut et vers le bas","Saut sur le côté"]
},
"CE1":{
"Français":["Les diphtongues (notion à préciser selon le support utilisé)","Vocabulaire fonctionnel : mots et expressions relatifs à l’homme et à sa santé","Reformuler des mots et expressions pour améliorer un portrait","Emploi de « ce » et « cette »","Lecture et compréhension d’un texte","Production écrite : améliorer une production"],
"Mathématiques — Arithmétique":["Numération et comparaison des nombres","Addition et soustraction","Multiplication : premières situations","Résolution de problèmes"],
"Mathématiques — Géométrie":["Reconnaître et décrire des figures planes","Segments et tracés géométriques"],
"Mathématiques — Mesures":["Mesures de longueur","Mesures de masse et de capacité","Lire l’heure"],
"Éducation sociale — Morale":["Respect et solidarité"],
"Éducation sociale — Civisme":["Droits et devoirs de l’élève"],
"Éducation sociale — Histoire-Géographie":["Le quartier ou le village","Repères du milieu de vie"],
"Éducation sociale — Langues et culture":["Langues et expressions du milieu"],
"EST":["Hygiène, alimentation et santé","Matériaux et objets du quotidien"],
"Éducation artistique — Dessin":["Dessiner à partir de formes simples"],
"Éducation artistique — Chant":["Chant collectif et rythme"],
"Éducation artistique — Travaux manuels":["Fabrication d’un objet simple"],
"Éducation artistique — Poésie":["Mémorisation et récitation d’un poème"],
"Éducation artistique — Conte":["Raconter les principaux événements d’un conte"],
"Éducation artistique — Couture":["Gestes de base et sécurité"],
"EPS":["Courir, sauter et lancer selon une consigne"]
},
"CE2":{
"Français":["Lecture et compréhension","Grammaire : identifier les constituants de la phrase","Conjugaison : formes verbales usuelles","Orthographe et vocabulaire","Production écrite"],
"Mathématiques — Arithmétique":["Numération et opérations","Multiplication et division dans des situations adaptées","Résolution de problèmes"],
"Mathématiques — Géométrie":["Figures planes et propriétés observables","Tracés à la règle"],
"Mathématiques — Mesures":["Longueurs, masses et capacités","Durées et calendrier"],
"Éducation sociale — Morale":["Responsabilité et solidarité"],
"Éducation sociale — Civisme":["Règles et symboles de la vie collective"],
"Éducation sociale — Histoire-Géographie":["Milieu local et activités humaines"],
"Éducation sociale — Langues et culture":["Patrimoine culturel local"],
"EST":["Hygiène et prévention","Objets techniques et matériaux"],
"Éducation artistique — Dessin":["Composition à partir de formes et lignes"],
"Éducation artistique — Chant":["Chant et expression rythmique"],
"Éducation artistique — Travaux manuels":["Réalisation d’un objet avec matériaux disponibles"],
"Éducation artistique — Poésie":["Récitation expressive"],
"Éducation artistique — Conte":["Structure et restitution du récit"],
"Éducation artistique — Couture":["Assemblage simple et sécurité"],
"EPS":["Coordination, course, saut et lancer"]
},
"CM1":{
"Français":["Compréhension et étude de textes","Grammaire et analyse de la phrase","Conjugaison et valeurs des temps","Orthographe et vocabulaire","Production de textes variés"],
"Mathématiques — Arithmétique":["Numération et opérations sur les nombres","Fractions et décimaux selon la progression","Résolution de problèmes"],
"Mathématiques — Géométrie":["Figures et solides","Angles, droites et tracés"],
"Mathématiques — Mesures":["Unités de longueur, masse et capacité","Périmètres et durées"],
"Éducation sociale — Morale":["Responsabilité et vie en communauté"],
"Éducation sociale — Civisme":["Citoyenneté et respect des biens communs"],
"Éducation sociale — Histoire-Géographie":["Repères historiques et géographiques du Bénin"],
"Éducation sociale — Langues et culture":["Patrimoine, langues et traditions"],
"EST":["Santé, environnement et prévention","Objets et techniques du milieu"],
"Éducation artistique — Dessin":["Composition et représentation"],
"Éducation artistique — Chant":["Chant choral et rythme"],
"Éducation artistique — Travaux manuels":["Conception et fabrication d’un objet"],
"Éducation artistique — Poésie":["Récitation et interprétation"],
"Éducation artistique — Conte":["Récit oral et expression"],
"Éducation artistique — Couture":["Techniques élémentaires et sécurité"],
"EPS":["Coordination et activités athlétiques adaptées"]
},
"CM2":{
"Français":["Lecture analytique et compréhension","Grammaire, conjugaison et orthographe","Vocabulaire et reformulation","Production de textes variés"],
"Mathématiques — Arithmétique":["Numération, opérations et problèmes complexes","Fractions et nombres décimaux selon la progression"],
"Mathématiques — Géométrie":["Construction de figures et propriétés","Solides et représentation"],
"Mathématiques — Mesures":["Conversions d’unités","Périmètre, aire et durées selon la progression"],
"Éducation sociale — Morale":["Engagement, responsabilité et solidarité"],
"Éducation sociale — Civisme":["Citoyenneté et préparation à la vie collective"],
"Éducation sociale — Histoire-Géographie":["Histoire et géographie du Bénin selon la progression"],
"Éducation sociale — Langues et culture":["Patrimoine et diversité culturelle"],
"EST":["Santé, environnement et techniques du quotidien"],
"Éducation artistique — Dessin":["Dessin d’observation et composition"],
"Éducation artistique — Chant":["Chant collectif et interprétation"],
"Éducation artistique — Travaux manuels":["Projet de fabrication et finition"],
"Éducation artistique — Poésie":["Récitation expressive"],
"Éducation artistique — Conte":["Narration et interprétation"],
"Éducation artistique — Couture":["Techniques de base et sécurité"],
"EPS":["Activités physiques, coordination et règles de sécurité"]
}
};

const $ = id => document.getElementById(id);

function escapeHTML(s){
 return String(s??"").replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
}
function initDisciplines(){
 $("discipline").innerHTML=disciplines.map(d=>`<option>${escapeHTML(d)}</option>`).join("");
 chargerNotions();
}
function chargerNotions(){
 const classe=$("classe").value, disc=$("discipline").value;
 const notions=(catalogue[classe]&&catalogue[classe][disc])||[];
 $("notionCatalogue").innerHTML='<option value="">— Choisir une notion —</option>'+notions.map(n=>`<option>${escapeHTML(n)}</option>`).join("");
}
function choisirNotion(){
 const n=$("notionCatalogue").value;
 if(n){$("titre").value=n;}
 const d=$("discipline").value;
 $("domaine").value=d.includes("Mathématiques")?d.split("—")[1].trim():d.split("—").slice(1).join("—").trim()||d;
 if($("classe").value==="CE1" && d==="Français" && n.includes("homme et à sa santé")){
  $("duree").value="45 min";
  $("competence").value="Écrire des textes de types et de fonctions variés.";
  $("connaissances").value="La vie des mots et expressions relatifs à l’homme et à sa santé.";
  $("strategies").value="Brainstorming ; travail individuel ; travail en groupe ; travail collectif.";
  $("materiel").value="Production de l’élève.";
  $("phase1").value="Rappel : rappeler le thème étudié en vocabulaire et les mots connus sur le portrait.";
  $("phase2").value="Mise en situation : l’élève a produit un texte sur une personne qui l’a impressionné par ses aspects physiques et moraux. Faire émerger le projet d’écriture et annoncer l’apprentissage.";
  $("phase3").value="Lire la production transcrite au tableau ; préciser le sens ; reformuler les idées avec des mots ou expressions appropriés ; retenir quelques reformulations ; repérer, épeler et écrire les mots choisis ; améliorer la production.";
  $("phase4").value="Réutiliser les mots ou expressions reformulés dans une phrase puis améliorer la production écrite.";
  $("phase5").value="Faire dire ce qui a été appris, ce qui a retenu l’attention et les difficultés rencontrées.";
  $("phase6").value="Évaluation orale : expliquer les mots ou expressions reformulés. Évaluation écrite : écrire correctement un mot ou une expression reformulée.";
  $("attendu3").value="Les élèves reformulent des mots et expressions adaptés au portrait et améliorent leur production.";
  $("attendu6").value="Les élèves expliquent oralement et écrivent correctement des mots ou expressions reformulés.";
 }
}
function val(id){return $(id).value.trim();}
function para(label,value){if(!value)return "";return `<p><strong>${escapeHTML(label)} :</strong> ${escapeHTML(value)}</p>`;}
function section(title,content){return content?`<section class="fiche-section"><h3>${escapeHTML(title)}</h3>${content}</section>`:"";}

function generer(){
 const titre=val("titre")||val("notionCatalogue");
 if(!titre){alert("Choisis une notion ou saisis le titre de la leçon.");$("titre").focus();return;}
 const classe=val("classe"),disc=val("discipline");
 const date=val("date")?new Date(val("date")+"T12:00:00").toLocaleDateString("fr-FR"):"";
 const metas=[
 ["Classe",classe],["Discipline",disc],["Domaine",val("domaine")],["Durée",val("duree")],
 ["Unité / période",val("unite")],["Situation d’apprentissage",val("sa")],["Séquence / séance",val("sequence")],
 ["Fiche N°",val("numero")],["Date",date],["École",val("ecole")],["Enseignant(e)",val("enseignant")],["Effectif",val("effectif")]
 ].filter(x=>x[1]);

 let html=`<div class="fiche-head"><h2>Fiche de préparation pédagogique</h2><h3>${escapeHTML(titre)}</h3><p>Bot pédagogique APC Bénin — modèle à adapter au guide de référence</p></div>`;
 html+=`<div class="meta">${metas.map(x=>`<div><strong>${escapeHTML(x[0])} :</strong> ${escapeHTML(x[1])}</div>`).join("")}</div>`;
 html+=section("I. CONTENUS DE FORMATION",
 para("Compétence disciplinaire",val("competence"))+
 para("Compétences transversales / transdisciplinaires",val("competencesTrans"))+
 para("Connaissances et techniques",val("connaissances"))+
 para("Objectif(s) d’apprentissage",val("objectif"))+
 para("Prérequis",val("prerequis"))+
 para("Stratégies d’enseignement / apprentissage / évaluation",val("strategies"))+
 para("Matériel",val("materiel"))+
 para("Situation de départ",val("situation")));

 const phases=[
 ["Activités préparatoires / rappel","phase1","attendu1"],
 ["Introduction / mise en situation","phase2","attendu2"],
 ["Réalisation / construction des savoirs","phase3","attendu3"],
 ["Application / entraînement","phase4","attendu4"],
 ["Retour / objectivation","phase5","attendu5"],
 ["Évaluation","phase6","attendu6"]
 ];
 const rows=phases.map(p=>`<tr><th>${escapeHTML(p[0])}</th><td>${escapeHTML(val(p[1]))}</td><td>${escapeHTML(val(p[2]))}</td></tr>`).join("");
 html+=`<section class="fiche-section"><h3>II. DÉROULEMENT</h3><table><thead><tr><th>Étapes / phases</th><th>Consignes et activités de l’enseignant / des élèves</th><th>Résultats attendus</th></tr></thead><tbody>${rows}</tbody></table>${val("consigne")?`<p><strong>Consigne / exercice d’évaluation :</strong> ${escapeHTML(val("consigne"))}</p>`:""}</section>`;
 html+=section("III. SYNTHÈSE / TRACE ÉCRITE",para("À retenir",val("trace")));
 html+=section("IV. REMÉDIATION ET PROJECTION",para("Remédiation / différenciation",val("remediation"))+para("Réinvestissement / projection",val("projection")));
 $("fiche").innerHTML=html;
 $("message").textContent="Fiche générée. Vérifie les informations et les consignes avant l’impression.";
}
function viderPreparation(){
 ["prerequis","objectif","situation","trace","remediation","projection","phase1","attendu1","phase2","attendu2","phase3","attendu3","phase4","attendu4","phase5","attendu5","phase6","attendu6","consigne"].forEach(id=>$(id).value="");
 $("message").textContent="Les champs de préparation ont été effacés.";
}
function texteFiche(){
 const node=$("fiche");
 return node.innerText||node.textContent||"";
}
$("classe").addEventListener("change",chargerNotions);
$("discipline").addEventListener("change",chargerNotions);
$("notionCatalogue").addEventListener("change",choisirNotion);
$("generer").addEventListener("click",generer);
$("vider").addEventListener("click",viderPreparation);
$("imprimer").addEventListener("click",()=>{
 if(!$("fiche").querySelector(".fiche-head")){alert("Génère d’abord la fiche.");return;}
 window.print();
});
$("copier").addEventListener("click",async()=>{
 if(!$("fiche").querySelector(".fiche-head")){alert("Génère d’abord la fiche.");return;}
 const t=texteFiche();
 try{
  await navigator.clipboard.writeText(t);
  $("message").textContent="Texte de la fiche copié.";
 }catch(e){
  const area=document.createElement("textarea");
  area.value=t;document.body.appendChild(area);area.select();
  const ok=document.execCommand("copy");area.remove();
  $("message").textContent=ok?"Texte de la fiche copié.":"Copie automatique indisponible : sélectionne le texte de la fiche et copie-le manuellement.";
 }
});
initDisciplines();
</script>
</body>
</html>
