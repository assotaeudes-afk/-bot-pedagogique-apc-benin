<!doctype html>
<html lang="fr">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Bot pédagogique APC Bénin</title>
<style>
:root{--v:#185d39;--c:#edf5ef;--o:#d5a53b;--ink:#202820;--muted:#647067;--line:#d9e2da}
*{box-sizing:border-box}
body{margin:0;background:#f2f5f2;color:var(--ink);font-family:Arial,Helvetica,sans-serif;line-height:1.45}
header{background:var(--v);color:#fff;padding:22px 16px;text-align:center}
header h1{margin:0 0 5px;font-size:clamp(22px,4vw,30px)}
header p{margin:0;color:#e6f1e9}
main{max-width:1100px;margin:22px auto;padding:0 14px}
.panel{background:#fff;border:1px solid var(--line);border-radius:12px;padding:18px;margin-bottom:18px;box-shadow:0 2px 8px #173b2410}
h2{color:var(--v);font-size:20px;margin:0 0 14px}
h3{color:var(--v);font-size:16px;margin:18px 0 8px}
.grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:12px}
.field{display:flex;flex-direction:column;gap:5px}
.field.full{grid-column:1/-1}
label{font-weight:700;font-size:13px}
input,select,textarea{width:100%;border:1px solid #bdcbbf;border-radius:7px;padding:10px;font:inherit;background:#fff;color:var(--ink)}
textarea{min-height:76px;resize:vertical}
.actions{display:flex;flex-wrap:wrap;gap:9px;margin-top:15px}
button{border:0;border-radius:8px;padding:11px 16px;font-weight:700;font-size:14px;cursor:pointer}
.primary{background:var(--v);color:#fff}.secondary{background:var(--c);color:var(--v);border:1px solid #c8ddce}.gold{background:var(--o);color:#2a2517}
.note{font-size:12px;color:var(--muted);margin-top:8px}
.warning{background:#fff8e8;border-left:4px solid var(--o);padding:10px 12px;border-radius:5px;font-size:13px;margin:10px 0}
#fiche{background:white}
.fiche-head{text-align:center;border-bottom:3px solid var(--v);padding-bottom:12px;margin-bottom:14px}
.fiche-head h2{font-size:22px;margin:0}
.fiche-head p{margin:4px 0;color:var(--muted);font-size:12px}
.meta{display:grid;grid-template-columns:repeat(3,1fr);gap:7px;margin:12px 0}
.meta div{border:1px solid var(--line);padding:7px;border-radius:5px;font-size:12px}
.meta b{color:var(--v)}
.info-grid{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.info{border:1px solid var(--line);padding:9px;border-radius:6px;font-size:13px;white-space:pre-wrap}
.info strong{display:block;color:var(--v);margin-bottom:3px}
table{width:100%;border-collapse:collapse;margin:8px 0 14px;font-size:12px}
th,td{border:1px solid #aebdaf;padding:8px;vertical-align:top;text-align:left}
th{background:var(--c);color:#174a2e}
.phase{font-weight:700;color:var(--v)}
.fiche-section{margin-top:15px}
.fiche-section h3{border-bottom:1px solid var(--line);padding-bottom:5px}
.fiche-section p{white-space:pre-wrap;margin:5px 0;font-size:13px}
footer{text-align:center;color:var(--muted);font-size:12px;padding:18px}
.empty{color:var(--muted);font-style:italic}
@media(max-width:650px){.grid,.info-grid{grid-template-columns:1fr}.meta{grid-template-columns:1fr 1fr}main{padding:0 9px}.panel{padding:13px}}
@page{size:A4 portrait;margin:12mm}
@media print{
 body{background:#fff;font-size:11px}
 header,.form-panel,.screen-actions,footer{display:none!important}
 main{max-width:none;margin:0;padding:0}
 .panel{border:0;box-shadow:none;padding:0;margin:0}
 #fiche{display:block!important}
 .fiche-head h2{font-size:18px}
 table{font-size:9px;page-break-inside:auto}
 tr{page-break-inside:avoid;page-break-after:auto}
 th,td{padding:5px}
 .fiche-section{page-break-inside:avoid}
}
</style>
</head>
<body>
<header>
  <h1>Bot pédagogique APC Bénin</h1>
  <p>Préparation des fiches pédagogiques du primaire</p>
</header>

<main>
<section class="panel form-panel">
<h2>Préparer une leçon</h2>
<div class="grid">
  <div class="field"><label for="classe">Classe</label>
    <select id="classe">
      <option>CI</option><option>CP</option><option>CE1</option><option>CE2</option><option>CM1</option><option>CM2</option>
    </select>
  </div>
  <div class="field"><label for="disc">Discipline</label>
    <select id="disc">
      <option>Français</option><option>Mathématiques</option><option>Éducation sociale</option><option>EST</option><option>Éducation artistique</option><option>EPS</option>
    </select>
  </div>
  <div class="field"><label for="dom">Domaine / sous-discipline</label><select id="dom"></select></div>
  <div class="field"><label for="notion">Notion / leçon</label><select id="notion"></select></div>
  <div class="field"><label for="type">Type de document</label>
    <select id="type">
      <option value="fiche">Fiche pédagogique complète</option>
      <option value="resume">Résumé de leçon</option>
      <option value="exercices">Exercices corrigés</option>
      <option value="evaluation">Évaluation avec barème et remédiation</option>
      <option value="pack">Pack complet : fiche, résumé, exercices et évaluation</option>
    </select>
  </div>
  <div class="field"><label for="duree">Durée (minutes)</label><input id="duree" type="number" min="10" max="180" value="30"></div>
  <div class="field"><label for="ecole">École</label><input id="ecole" placeholder="Nom de l'école"></div>
  <div class="field"><label for="enseignant">Enseignant(e)</label><input id="enseignant" placeholder="Nom de l'enseignant(e)"></div>
  <div class="field"><label for="date">Date</label><input id="date" type="date"></div>
  <div class="field"><label for="periode">Période / trimestre</label><input id="periode" placeholder="Ex. : 1er trimestre"></div>
  <div class="field full"><label for="competence">Compétence(s) visée(s)</label><textarea id="competence" placeholder="Compétence(s) travaillée(s)"></textarea></div>
  <div class="field full"><label for="objectif">Objectif spécifique / résultats attendus</label><textarea id="objectif" placeholder="À la fin de la séance, l'apprenant sera capable de..."></textarea></div>
  <div class="field"><label for="prerequis">Prérequis</label><textarea id="prerequis" placeholder="Acquis antérieurs nécessaires"></textarea></div>
  <div class="field"><label for="materiel">Matériel / supports</label><textarea id="materiel" placeholder="Ardoises, images, objets, manuel..."></textarea></div>
  <div class="field full"><label for="situation">Situation de départ / situation-problème</label><textarea id="situation" placeholder="Décrire la situation déclenchante"></textarea></div>
  <div class="field full"><label for="observation">Observations ou adaptation souhaitée (facultatif)</label><textarea id="observation" placeholder="Besoins particuliers, différenciation..."></textarea></div>
</div>
<div class="warning" id="sourceWarning">Les propositions générales doivent être adaptées au programme et au guide pédagogique utilisés dans votre école.</div>
<div class="actions screen-actions">
  <button class="primary" id="generate">Générer la fiche</button>
  <button class="secondary" id="reset">Réinitialiser</button>
</div>
<p class="note">Les contenus signalés comme propositions sont des aides à la préparation. Vérifiez toujours les formulations et la progression avec les documents pédagogiques de référence.</p>
</section>

<section class="panel" id="resultPanel">
<div class="actions screen-actions">
  <button class="secondary" id="copy">Copier le document</button>
  <button class="gold" id="print">Imprimer / PDF</button>
</div>
<article id="fiche"><p class="empty">Votre fiche pédagogique apparaîtra ici après avoir appuyé sur « Générer la fiche ».</p></article>
</section>
</main>
<footer>Bot pédagogique APC Bénin — outil d'aide à la préparation pédagogique</footer>

<script>
"use strict";
const $ = id => document.getElementById(id);

const D = {
 "Français":{
  "Lecture et sons":["Les voyelles","Les consonnes","Les syllabes","Les mots","Les phrases","Compréhension de texte"],
  "Langage oral":["Écouter et comprendre","S'exprimer oralement","Décrire une image"],
  "Écriture":["Graphisme","Copie de lettres et de mots","Production écrite"],
  "Grammaire et vocabulaire":["Le nom","Le verbe","Le masculin et le féminin","Le singulier et le pluriel","Le vocabulaire"]
 },
 "Mathématiques":{
  "Arithmétique":["Dénombrement","Les nombres","Comparer des nombres","Addition","Soustraction","Multiplication","Partage et division"],
  "Géométrie":["Les lignes","Les formes géométriques","Les solides","Se repérer dans l'espace"],
  "Mesures":["Longueurs","Masses","Capacités","Temps","Monnaie"]
 },
 "Éducation sociale":{
  "ES-Morale":["Les règles de vie","Le respect","La solidarité","La propreté"],
  "ES-Civisme":["Les droits et devoirs","Les symboles nationaux","La vie en communauté"],
  "ES-Histoire-Géographie":["La famille","Le village et le quartier","Le Bénin","L'environnement"],
  "ES-Langues et culture":["Les salutations","Les traditions","Les valeurs culturelles"]
 },
 "EST":{
  "Éducation scientifique et technologique":["Le corps humain","Les animaux","Les plantes","L'eau","L'air","L'hygiène","Les objets techniques"]
 },
 "Éducation artistique":{
  "Dessin":["Les lignes et les formes","Dessin d'observation","Les couleurs"],
  "Chant":["Chant et rythme","Apprentissage d'un chant"],
  "Travaux manuels":["Pliage","Découpage et collage","Modelage"],
  "Poésie":["Récitation d'une poésie"],
  "Conte":["Écoute et compréhension d'un conte"],
  "Couture":["Initiation aux points simples"]
 },
 "EPS":{
  "Activités motrices":["Courir","Sauter","Lancer","Jeux collectifs","Équilibre et coordination"]
 }
};

const FR_CI = {
 "Leçon 1 : Apprentissage de la lettre-son A":{
  title:"Apprentissage de la lettre-son A",
  objective:"Reconnaître, prononcer et écrire la lettre A sous ses différentes formes.",
  competence:"Développer les premiers apprentissages de lecture et d'écriture par l'identification et la reproduction d'une lettre-son.",
  prerequisite:"Écouter une consigne simple et observer des signes ou des images.",
  material:"Manuel et guide de français CI, tableau, cartes portant la lettre A, ardoises et craies.",
  stages:[
   ["Révision / mise en disponibilité","Mettre les apprenants en situation d'écoute et d'observation. Faire rappeler les règles de travail.","Écoutent, observent et répondent aux questions simples.","Être attentif et observer les supports."],
   ["Découverte de la lettre-son A","Présenter la lettre A dans ses différentes formes. Faire observer et prononcer le son.","Observent, identifient et prononcent A.","Montrer la lettre A et dire le son entendu."],
   ["Discrimination visuelle et auditive","Faire distinguer A parmi d'autres signes et faire repérer le son dans des mots proposés oralement.","Repèrent A et écoutent les mots proposés.","Identifier la lettre A sans la confondre avec les autres signes."],
   ["Écriture / entraînement","Montrer le tracé de A dans l'air, puis au tableau. Guider le tracé sur ardoise et cahier.","Tracent dans l'air, sur l'ardoise puis sur le cahier.","Reproduire correctement la lettre A."],
   ["Évaluation et remédiation","Faire reconnaître et écrire A individuellement. Corriger les difficultés observées.","Identifient et écrivent A individuellement.","Reconnaître et écrire A sous les formes étudiées."]
  ],
  trace:"La lettre A est une lettre de l'alphabet. On apprend à la reconnaître, à prononcer son son et à l'écrire sous ses différentes formes.",
  exercise:"1. Entoure la lettre A parmi plusieurs lettres proposées.\n2. Prononce le son étudié.\n3. Trace la lettre A dans l'air puis sur ton ardoise.",
  correction:"L'apprenant doit identifier uniquement la lettre A et reproduire un tracé reconnaissable.",
  caution:"Pour cette première leçon sur la lettre-son A, le guide indique de ne pas former de syllabes, de mots ou de phrases à ce stade."
 },
 "Leçon 2 : Apprentissage de la lettre L":{
  title:"Apprentissage de la lettre L",
  objective:"Reconnaître, prononcer et écrire la lettre L ; former des syllabes et des mots simples contenant L ; lire des mots et des phrases simples.",
  competence:"Lire et écrire des éléments simples en mobilisant les lettres-sons déjà étudiées.",
  prerequisite:"Avoir travaillé les apprentissages antérieurs de lettres-sons prévus dans la progression.",
  material:"Guide et manuel de français CI, tableau, cartes-lettres, ardoises et cahiers.",
  stages:[
   ["Révision","Faire réviser les lettres-sons déjà étudiées et leurs sons.","Reconnaissent et prononcent les éléments rappelés.","Répondre oralement et identifier les lettres révisées."],
   ["Découverte de L","Présenter L, faire observer sa forme et écouter sa prononciation.","Observent et prononcent L.","Reconnaître et prononcer la lettre L."],
   ["Écriture","Démontrer le tracé puis guider les essais.","Tracent L dans l'air, au tableau ou sur l'ardoise.","Écrire la lettre L lisiblement."],
   ["Formation et lecture","Guider la formation de syllabes et de mots simples contenant L, puis leur lecture.","Composent et lisent les éléments proposés.","Former et lire des syllabes et mots simples contenant L."],
   ["Évaluation","Faire lire et écrire individuellement ; reprendre les erreurs.","Lis­ent et écrivent individuellement.","Montrer la maîtrise des objectifs de la séance."]
  ],
  trace:"La lettre L se reconnaît à sa forme et au son qu'elle représente. Elle peut être utilisée avec les lettres déjà étudiées pour former des syllabes et des mots simples.",
  exercise:"1. Entoure la lettre L.\n2. Écris L plusieurs fois.\n3. Lis les syllabes et mots construits en classe avec les lettres déjà étudiées.",
  correction:"Vérifier la reconnaissance, la prononciation, le tracé et la lecture des éléments effectivement construits pendant la séance."
 },
 "Leçon 3 : Apprentissage de la lettre-son T":{
  title:"Apprentissage de la lettre-son T",
  objective:"Reconnaître, prononcer et écrire T ; former des syllabes et des mots simples contenant T ; lire des mots et des phrases simples comportant T.",
  competence:"Mobiliser les lettres-sons étudiées pour lire et écrire des syllabes, des mots et de courtes phrases.",
  prerequisite:"Réviser les lettres-sons déjà étudiées dans la progression.",
  material:"Guide et manuel de français CI, tableau, cartes-lettres, ardoises et cahiers.",
  stages:[
   ["Révision","Faire identifier et prononcer les lettres-sons précédemment étudiées.","Rappellent les lettres et les sons connus.","Identifier et prononcer les éléments révisés."],
   ["Découverte de T","Présenter la lettre-son T et conduire l'observation visuelle et auditive.","Observent, identifient et prononcent T.","Reconnaître et prononcer T."],
   ["Écriture","Démontrer le tracé de T puis accompagner les essais.","Tracent la lettre dans l'air, au tableau et sur l'ardoise.","Écrire T correctement."],
   ["Syllabes, mots et phrases","Faire construire et lire des syllabes, mots et phrases simples avec les lettres déjà étudiées.","Composent, lisent et relisent les éléments proposés.","Lire les éléments simples contenant T."],
   ["Évaluation et remédiation","Évaluer reconnaissance, prononciation, écriture et lecture ; reprendre les difficultés.","Réalisent les tâches individuellement.","Atteindre les objectifs annoncés."]
  ],
  trace:"La lettre T représente un son que l'on apprend à reconnaître, à prononcer et à écrire. Avec les lettres déjà étudiées, elle permet de lire des syllabes, des mots et de courtes phrases.",
  exercise:"1. Repère la lettre T.\n2. Écris T.\n3. Lis les syllabes, mots et phrases construits en classe avec les lettres connues.",
  correction:"La correction porte sur l'identification, la prononciation, le tracé et la lecture des éléments travaillés."
 },
 "Leçon 4 : Apprentissage de la lettre-son O":{
  title:"Apprentissage de la lettre-son O",
  objective:"Reconnaître, prononcer et écrire O ; former des syllabes et des mots simples contenant O ; lire des mots et des phrases simples.",
  competence:"Développer la lecture et l'écriture à partir de lettres-sons et de combinaisons déjà étudiées.",
  prerequisite:"Réviser les lettres-sons antérieurement étudiées.",
  material:"Guide et manuel de français CI, tableau, cartes-lettres, ardoises et cahiers.",
  stages:[
   ["Révision","Faire rappeler les lettres-sons déjà étudiées.","Identifient et prononcent les lettres connues.","Répondre aux sollicitations de révision."],
   ["Découverte de O","Présenter O et faire observer sa forme et son son.","Observent, identifient et prononcent O.","Reconnaître et prononcer O."],
   ["Écriture","Démontrer le tracé de O et guider les apprenants.","Tracent O dans l'air et sur l'ardoise.","Écrire O de manière lisible."],
   ["Syllabes, mots et lecture","Faire construire des syllabes et mots simples avec les lettres déjà étudiées, puis organiser la lecture.","Composent et lisent les éléments proposés.","Lire les syllabes et mots contenant O."],
   ["Évaluation","Faire reconnaître, lire et écrire les éléments travaillés.","Réalisent les exercices individuellement.","Montrer les acquis et identifier les difficultés."]
  ],
  trace:"La lettre O se reconnaît à sa forme et au son étudié. Elle s'associe aux lettres déjà apprises pour former des syllabes et des mots simples.",
  exercise:"1. Entoure O.\n2. Écris O.\n3. Lis les syllabes et les mots étudiés en classe.",
  correction:"Vérifier la reconnaissance de O, son écriture et la lecture des combinaisons effectivement étudiées."
 },
 "Leçon 5 : Apprentissage de la lettre-son P":{
  title:"Apprentissage de la lettre-son P",
  objective:"Reconnaître, prononcer et écrire P ; former des syllabes et des mots simples contenant P ; lire des mots et des phrases simples.",
  competence:"Lire et écrire des syllabes, des mots et des phrases simples en mobilisant les lettres-sons connues.",
  prerequisite:"Réviser les lettres-sons déjà étudiées dans le guide.",
  material:"Guide et manuel de français CI, tableau, cartes-lettres, ardoises et cahiers.",
  stages:[
   ["Révision","Faire réviser les lettres-sons précédemment étudiées.","Identifient et prononcent les lettres connues.","Rappeler les acquis utiles."],
   ["Découverte de P","Présenter la lettre P, sa forme et son son.","Observent, identifient et prononcent P.","Reconnaître et prononcer P."],
   ["Écriture","Montrer le tracé et guider la reproduction.","Tracent P dans l'air puis sur l'ardoise.","Écrire P lisiblement."],
   ["Syllabes, mots et phrases","Guider la construction et la lecture d'éléments simples avec les lettres connues.","Composent et lisent les éléments proposés.","Lire des éléments contenant P."],
   ["Évaluation et remédiation","Faire réaliser une tâche individuelle puis corriger les difficultés.","Lis­ent, identifient et écrivent individuellement.","Atteindre les objectifs annoncés."]
  ],
  trace:"La lettre P représente un son. On apprend à la reconnaître, à la prononcer et à l'écrire. Elle permet de former des syllabes et des mots avec les lettres déjà étudiées.",
  exercise:"1. Repère P parmi d'autres lettres.\n2. Écris P.\n3. Lis les syllabes et mots construits avec les lettres connues.",
  correction:"Vérifier la reconnaissance, la prononciation, l'écriture et la lecture des éléments étudiés."
 }
};

function populateDomains(){
 const disc=$("disc").value, dom=$("dom"), old=dom.value;
 dom.innerHTML="";
 Object.keys(D[disc]).forEach(x=>dom.add(new Option(x,x)));
 if([...dom.options].some(x=>x.value===old))dom.value=old;
 populateNotions();
}
function populateNotions(){
 const disc=$("disc").value, domain=$("dom").value, s=$("notion"), old=s.value;
 s.innerHTML="";
 let items=(D[disc]&&D[disc][domain])?D[disc][domain]:[];
 if($("classe").value==="CI" && disc==="Français" && domain==="Lecture et sons"){
   items=Object.keys(FR_CI);
 }
 items.forEach(x=>s.add(new Option(x,x)));
 if([...s.options].some(x=>x.value===old))s.value=old;
 updateSourceNotice();
}
function updateSourceNotice(){
 const isFR=$("classe").value==="CI" && $("disc").value==="Français" && $("dom").value==="Lecture et sons";
 const isMath=$("classe").value==="CI" && $("disc").value==="Mathématiques";
 $("sourceWarning").textContent=isFR
 ? "Contenu adapté aux leçons A, L, T, O et P relevées dans le Guide pédagogique du manuel Réussir en français au CI (LAHA Éditions, 2024). Les activités sont reformulées et les exemples doivent être vérifiés dans le manuel."
 : isMath
 ? "Pour le CI en mathématiques, privilégier la manipulation concrète, la représentation, la symbolisation, puis l'objectivation et le réinvestissement. Vérifier la notion avec le guide utilisé."
 : "Catalogue indicatif : les notions et formulations doivent être vérifiées avec les programmes et guides pédagogiques en vigueur au Bénin.";
}
function distribute(total,n){
 const base=Math.floor(total/n), rest=total-base*n;
 return Array.from({length:n},(_,i)=>base+(i<rest?1:0));
}
function escapeHTML(s){
 return String(s??"").replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
}
function getGenericStages(){
 if($("classe").value==="CI" && $("disc").value==="Mathématiques"){
  return [
   ["Introduction","Activer les connaissances antérieures et présenter la situation-problème.","Écoutent, observent et mobilisent leurs acquis.","Comprendre la situation et dire ce qui est recherché."],
   ["Réalisation : manipulation","Organiser la recherche avec du matériel concret et guider les essais.","Manipulent, essaient, comparent et expliquent.","Résoudre la situation par la manipulation."],
   ["Réalisation : représentation et abstraction","Faire passer de la manipulation aux dessins, puis aux signes ou procédures adaptés.","Représentent et formalisent les résultats.","Exprimer la démarche avec des représentations ou symboles."],
   ["Entraînement guidé et autonome","Faire un exemple, accompagner un exercice puis proposer une tâche individuelle.","Travaillent avec aide puis individuellement.","Appliquer la procédure à une tâche nouvelle."],
   ["Retour / réinvestissement","Faire verbaliser ce qui a été appris et proposer une courte évaluation.","Expliquent leur démarche et répondent à l'évaluation.","Dire ce qui a été appris et réutiliser l'acquis."]
  ];
 }
 return [
  ["Mise en situation / rappel","Présenter une situation motivante, rappeler les acquis et annoncer l'objectif.","Observent, écoutent, répondent et mobilisent leurs acquis.","Comprendre la situation et faire le lien avec les acquis."],
  ["Recherche et exploration","Donner une consigne claire, organiser les recherches individuelles ou en groupes et accompagner.","Cherchent, manipulent, échangent et proposent des réponses.","Produire une première réponse ou démarche."],
  ["Mise en commun","Faire présenter les démarches, comparer les propositions et guider les échanges.","Présentent, écoutent, comparent et justifient.","Expliquer et confronter les réponses."],
  ["Structuration / synthèse","Faire dégager l'essentiel et formaliser la notion avec les apprenants.","Formulent la règle, la notion ou la démarche et prennent trace.","Énoncer ce qui est à retenir."],
  ["Application / entraînement","Proposer des tâches progressives et accompagner les apprenants.","Appliquent la notion à des exercices.","Réussir une tâche d'application."],
  ["Évaluation / clôture","Vérifier les acquis, corriger les erreurs et proposer une remédiation.","Réalisent l'évaluation et corrigent leurs erreurs.","Montrer les acquis et identifier ce qui reste à travailler."]
 ];
}
function renderTable(stages,total){
 const times=distribute(total,stages.length);
 return `<table><thead><tr><th style="width:17%">Phase / durée</th><th style="width:29%">Activités de l'enseignant</th><th style="width:25%">Activités des apprenants</th><th style="width:29%">Consignes / résultats attendus</th></tr></thead><tbody>${
 stages.map((s,i)=>`<tr><td><span class="phase">${escapeHTML(s[0])}</span><br>${times[i]} min</td><td>${escapeHTML(s[1])}</td><td>${escapeHTML(s[2])}</td><td>${escapeHTML(s[3])}</td></tr>`).join("")
 }</tbody></table>`;
}
function section(title,content){
 return `<section class="fiche-section"><h3>${title}</h3><p>${escapeHTML(content||"À compléter selon la séance.")}</p></section>`;
}
function generate(){
 const classe=$("classe").value, disc=$("disc").value, domain=$("dom").value, notion=$("notion").value;
 const type=$("type").value, total=Math.max(10,Number($("duree").value)||30);
 const special=(classe==="CI"&&disc==="Français"&&FR_CI[notion])?FR_CI[notion]:null;
 let objective=$("objectif").value.trim()||(special?special.objective:`À la fin de la séance, l'apprenant sera capable de traiter correctement la notion : ${notion}.`);
 let competence=$("competence").value.trim()||(special?special.competence:`Mobiliser les ressources nécessaires pour réaliser une tâche liée à ${notion}.`);
 let prerequisite=$("prerequis").value.trim()||(special?special.prerequisite:"Acquis antérieurs en rapport avec la notion.");
 let material=$("materiel").value.trim()||(special?special.material:"Tableau, ardoises, cahiers, matériel concret et supports adaptés à la notion.");
 let stages=special?special.stages:getGenericStages();
 let title=special?special.title:notion;
 let warning=special?`<div class="warning">${escapeHTML(special.caution||"Activités reformulées à partir des objectifs et étapes du guide pédagogique. Vérifier les exemples dans le manuel.")}</div>`:"<div class=\"warning\">Proposition pédagogique indicative : adapter les phases, les contenus et les évaluations au programme officiel, au guide de l'enseignant et au niveau réel des apprenants.</div>";
 const meta=[
  ["École",$("ecole").value],["Enseignant(e)",$("enseignant").value],["Classe",classe],
  ["Discipline",disc],["Domaine",domain],["Date",$("date").value],["Période",$("periode").value],["Durée",total+" minutes"],["Leçon",title]
 ];
 let out=`<div class="fiche-head"><h2>FICHE PÉDAGOGIQUE APC</h2><p>République du Bénin — Enseignement primaire</p></div>
 <div class="meta">${meta.map(x=>`<div><b>${escapeHTML(x[0])} :</b> ${escapeHTML(x[1]||"Non renseigné")}</div>`).join("")}</div>
 ${warning}
 <div class="info-grid">
  <div class="info"><strong>Compétence(s) visée(s)</strong>${escapeHTML(competence)}</div>
  <div class="info"><strong>Objectif spécifique / résultats attendus</strong>${escapeHTML(objective)}</div>
  <div class="info"><strong>Prérequis</strong>${escapeHTML(prerequisite)}</div>
  <div class="info"><strong>Matériel et supports</strong>${escapeHTML(material)}</div>
  <div class="info" style="grid-column:1/-1"><strong>Situation de départ / situation-problème</strong>${escapeHTML($("situation").value.trim()||"L'enseignant présente une situation adaptée à l'environnement des apprenants et en lien avec la notion.")}</div>
 </div>`;
 const isOnlyResume=type==="resume", onlyExercises=type==="exercices";
 if(!isOnlyResume&&!onlyExercises){
  out+=`<div class="fiche-section"><h3>Déroulement de la séance</h3>${renderTable(stages,total)}</div>`;
 }
 const trace=special?special.trace:`À retenir : ${notion} — retenir la notion, la démarche ou la règle construite pendant la séance.`;
 const ex=special?special.exercise:`1. Proposer une tâche simple de reconnaissance ou d'application de « ${notion} ».\n2. Réaliser un exercice d'application adapté au niveau.\n3. Expliquer la démarche utilisée.`;
 const corr=special?special.correction:"Correction attendue : réponses exactes, démarche compréhensible et justification adaptée au niveau.";
 if(type==="resume"||type==="pack")out+=section("Résumé / trace écrite",trace);
 if(type==="exercices"||type==="pack")out+=section("Exercices d'application",ex)+section("Correction proposée",corr);
 if(type==="evaluation"||type==="pack"||type==="fiche"){
  out+=section("Évaluation",`Critères : compréhension de la consigne, exactitude de la réponse, démarche et autonomie. Prévoir 2 à 3 tâches adaptées à l'objectif : ${objective}`);
  out+=section("Barème indicatif","Exercice 1 : 4 points ; exercice 2 : 3 points ; exercice 3 : 3 points. Total : 10 points. Adapter le barème au nombre de tâches et aux exigences de la leçon.");
  out+=section("Remédiation","Reprendre la difficulté observée avec une explication plus simple, une démonstration, du matériel concret ou un exercice guidé. Faire ensuite vérifier l'acquis par une tâche courte.");
 }
 if(type==="fiche"||type==="pack"||type==="resume"){
  out+=section("Bilan / observations",$("observation").value.trim()||"Noter les réussites, les difficultés rencontrées et les apprenants nécessitant un accompagnement.");
  out+=section("Prolongement / travail à faire","Proposer une activité courte de réinvestissement en lien direct avec la leçon et adaptée au niveau des apprenants.");
 }
 $("fiche").innerHTML=out;
 $("resultPanel").scrollIntoView({behavior:"smooth",block:"start"});
}
async function copyDocument(){
 const textContent=$("fiche").innerText;
 if(!textContent||textContent.includes("apparaîtra ici")){alert("Générez d'abord une fiche.");return;}
 try{
  if(navigator.clipboard&&window.isSecureContext){await navigator.clipboard.writeText(textContent);}
  else{
   const area=document.createElement("textarea");area.value=textContent;document.body.appendChild(area);area.select();
   const ok=document.execCommand("copy");area.remove();if(!ok)throw new Error("Copie non disponible");
  }
  alert("Document copié.");
 }catch(e){alert("La copie automatique n'a pas fonctionné. Sélectionnez le texte de la fiche et copiez-le manuellement.");}
}
function resetForm(){
 $("ecole").value="";$("enseignant").value="";$("date").value="";$("periode").value="";
 $("competence").value="";$("objectif").value="";$("prerequis").value="";$("materiel").value="";
 $("situation").value="";$("observation").value="";$("duree").value=30;
 $("type").value="fiche";$("classe").value="CI";$("disc").value="Français";populateDomains();
 $("fiche").innerHTML='<p class="empty">Votre fiche pédagogique apparaîtra ici après avoir appuyé sur « Générer la fiche ».</p>';
}
$("disc").addEventListener("change",populateDomains);
$("dom").addEventListener("change",populateNotions);
$("classe").addEventListener("change",populateNotions);
$("generate").addEventListener("click",generate);
$("copy").addEventListener("click",copyDocument);
$("print").addEventListener("click",()=>window.print());
$("reset").addEventListener("click",resetForm);
populateDomains();
</script>
</body>
</html>
