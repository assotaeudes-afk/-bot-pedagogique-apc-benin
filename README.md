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
      <option>CI</option><option selected>CP</option><option>CE1</option><option>CE2</option><option>CM1</option><option>CM2</option>
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
  "Arithmétique":[
   "Constituer et dénombrer une collection",
   "Comparer des collections : autant, plus, moins",
   "Associer une quantité à une représentation",
   "Reconnaître et construire les nombres étudiés",
   "Lire et écrire les nombres étudiés",
   "Ranger et comparer des nombres",
   "Décomposer et recomposer des nombres",
   "Additionner par manipulation",
   "Soustraire par manipulation",
   "Résoudre de petits problèmes additifs"
  ],
  "Géométrie":[
   "Se repérer dans l'espace : devant et derrière",
   "Se repérer dans l'espace : dessus et dessous",
   "Se repérer dans l'espace : entre et à côté",
   "Reconnaître et tracer des lignes",
   "Reconnaître et reproduire un cercle",
   "Reconnaître et reproduire un carré",
   "Reconnaître et reproduire un triangle",
   "Classer et assembler des formes géométriques",
   "Reproduire un assemblage de formes"
  ],
  "Mesures":[
   "Comparer des longueurs : long et court",
   "Comparer des longueurs : plus long et plus court",
   "Comparer des masses : lourd et léger",
   "Comparer des contenances : plein et vide",
   "Comparer des contenances : plus et moins",
   "Se repérer dans le temps : matin, midi et soir",
   "Se repérer dans la journée et la semaine",
   "Comparer des durées par observation",
   "Utiliser des unités non conventionnelles pour mesurer",
   "Découvrir des situations simples d'échange et de monnaie"
  ]
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
  exercise:"1. Entoure la lettre A parmi plusieurs lettres proposées.__EXERCISE_NL__2. Prononce le son étudié.__EXERCISE_NL__3. Trace la lettre A dans l'air puis sur ton ardoise.",
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
  exercise:"1. Entoure la lettre L.__EXERCISE_NL__2. Écris L plusieurs fois.__EXERCISE_NL__3. Lis les syllabes et mots construits en classe avec les lettres déjà étudiées.",
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
  exercise:"1. Repère la lettre T.__EXERCISE_NL__2. Écris T.__EXERCISE_NL__3. Lis les syllabes, mots et phrases construits en classe avec les lettres connues.",
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
  exercise:"1. Entoure O.__EXERCISE_NL__2. Écris O.__EXERCISE_NL__3. Lis les syllabes et les mots étudiés en classe.",
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
  exercise:"1. Repère P parmi d'autres lettres.__EXERCISE_NL__2. Écris P.__EXERCISE_NL__3. Lis les syllabes et mots construits avec les lettres connues.",
  correction:"Vérifier la reconnaissance, la prononciation, l'écriture et la lecture des éléments étudiés."
 }
};

// Banque pédagogique indicative pour les Mathématiques au CI.
// La progression numérique exacte doit être ajustée au guide utilisé en classe.
const MATH_CI = {
 "Arithmétique":{
  "Constituer et dénombrer une collection":{
   objective:"Constituer une collection et déterminer sa quantité en dénombrant les objets un à un.", prerequisite:"Observer, manipuler et distinguer des objets.", material:"Graines, bouchons, bâtonnets, cailloux, cartes-images et ardoises.",
   situation:"Sur une table, l'enseignant dépose un ensemble d'objets et demande aux apprenants de préparer une collection ayant la même quantité.",
   stages:[
    ["Introduction","Présenter deux collections et demander comment savoir combien d'objets elles contiennent.","Observent, proposent des idées et formulent le problème.","Dire comment déterminer la quantité d'une collection."],
    ["Manipulation concrète","Distribuer des objets. Faire déplacer ou pointer chaque objet une seule fois pendant le comptage.","Manipulent, séparent les objets déjà comptés et énoncent la suite orale connue.","Dénombrer sans oublier ni compter deux fois un objet."],
    ["Représentation","Faire représenter la collection par des dessins ou des marques, puis comparer les représentations.","Dessinent ou font des marques correspondant aux objets.","Faire correspondre chaque objet à une représentation."],
    ["Abstraction / symbolisation","Associer la quantité obtenue à la représentation chiffrée correspondante, uniquement dans la plage de nombres déjà étudiée.","Associent la collection, le dessin et le nombre présenté.","Relier quantité, représentation et écriture chiffrée connue."],
    ["Objectivation et réinvestissement","Faire expliquer la méthode puis proposer une nouvelle collection à dénombrer.","Expliquent leur démarche et dénombrent une nouvelle collection.","Dénombrer de façon organisée et expliquer comment faire."]
   ], trace:"Pour dénombrer une collection, je compte chaque objet une seule fois. Je peux déplacer ou pointer les objets déjà comptés.", exercise:"1. Dénombre les objets d'une collection préparée par le maître.__EXERCISE_NL__2. Prépare une collection qui contient autant d'objets que le modèle.__EXERCISE_NL__3. Représente la collection par des dessins.", correction:"La réponse correspond au nombre réel d'objets. Chaque objet doit être compté une seule fois. Adapter les quantités aux nombres déjà étudiés."
  },
  "Comparer des collections : autant, plus, moins":{
   objective:"Comparer deux collections par correspondance terme à terme et employer autant que, plus que ou moins que.", prerequisite:"Constituer et dénombrer de petites collections.", material:"Bouchons, graines, jetons, images et deux plateaux.",
   situation:"Deux groupes d'apprenants reçoivent des collections d'objets. Ils cherchent à savoir quel groupe en a le plus, le moins ou autant.",
   stages:[
    ["Introduction","Présenter deux collections visiblement différentes ou proches et poser la question de comparaison.","Observent et émettent des hypothèses.","Identifier ce qu'il faut comparer."],
    ["Manipulation concrète","Faire associer chaque objet d'une collection à un objet de l'autre collection.","Apparient les objets un à un et observent les objets restants.","Comparer sans se fier uniquement à la taille ou à la disposition."],
    ["Représentation","Faire dessiner les deux collections et les associations réalisées.","Dessinent et relient les éléments correspondants.","Représenter la comparaison terme à terme."],
    ["Abstraction / symbolisation","Introduire oralement les expressions autant que, plus que et moins que à partir des manipulations.","Formulent la comparaison avec les mots appropriés.","Employer correctement les mots de comparaison."],
    ["Objectivation et réinvestissement","Proposer de nouvelles collections et demander une justification.","Comparent et expliquent leur réponse.","Comparer deux collections et justifier le résultat."]
   ], trace:"Deux collections ont autant d'objets si chaque objet de l'une peut être associé à un objet de l'autre sans reste. Une collection peut avoir plus ou moins d'objets.", exercise:"1. Compare deux collections avec des objets.__EXERCISE_NL__2. Dis laquelle en a le plus ou le moins.__EXERCISE_NL__3. Trouve deux collections qui ont autant d'objets.", correction:"Vérifier la correspondance terme à terme et l'emploi correct de autant que, plus que ou moins que."
  },
  "Additionner par manipulation":{
   objective:"Réunir deux petites collections et déterminer la quantité totale par manipulation.", prerequisite:"Dénombrer de petites collections et comprendre l'idée de réunion.", material:"Graines, jetons, bouchons, dessins et cartes-nombres étudiées.",
   situation:"Un apprenant possède une petite collection d'objets et en reçoit une autre. La classe cherche combien il en possède maintenant.",
   stages:[
    ["Introduction","Présenter une situation de réunion de deux collections et faire exprimer la question.","Écoutent, observent et identifient les deux quantités à réunir.","Comprendre qu'il faut réunir deux collections."],
    ["Manipulation concrète","Faire réunir les deux collections puis compter tous les objets.","Rassemblent les objets et dénombrent la collection obtenue.","Trouver le total par manipulation et comptage."],
    ["Représentation","Faire dessiner les deux groupes puis la collection réunie.","Représentent les deux quantités et leur réunion.","Passer des objets à un dessin organisé."],
    ["Abstraction / symbolisation","Présenter le signe + et une écriture additive seulement avec les nombres déjà étudiés.","Associent l'action de réunir à l'écriture proposée.","Comprendre le sens de l'addition comme réunion."],
    ["Objectivation et réinvestissement","Faire expliquer la démarche et proposer une autre situation concrète.","Expliquent et résolvent une nouvelle situation.","Réinvestir l'addition dans un problème simple."]
   ], trace:"Additionner, c'est réunir des quantités pour trouver le total. On peut d'abord réunir les objets, puis les compter.", exercise:"1. Réunis deux petites collections.__EXERCISE_NL__2. Compte tous les objets.__EXERCISE_NL__3. Représente la situation par un dessin et, si cela a été étudié, par une écriture avec le signe +.", correction:"Le total doit correspondre au dénombrement de la collection réunie. Utiliser uniquement les nombres et écritures déjà étudiés."
  },
  "Soustraire par manipulation":{
   objective:"Retirer une partie d'une collection et déterminer la quantité qui reste.", prerequisite:"Dénombrer une collection et comprendre l'action de retirer.", material:"Jetons, graines, bouchons, cartes-images et ardoises.",
   situation:"Une collection d'objets est présentée. Une partie est retirée ; les apprenants doivent déterminer combien d'objets restent.",
   stages:[
    ["Introduction","Présenter la collection et raconter une situation où l'on retire quelques objets.","Écoutent, observent et identifient la question.","Comprendre la recherche de la quantité restante."],
    ["Manipulation concrète","Faire dénombrer la collection de départ, retirer les objets indiqués et compter ceux qui restent.","Comptent, retirent les objets et dénombrent le reste.","Déterminer le reste en manipulant."],
    ["Représentation","Faire dessiner la collection initiale, barrer les objets retirés et compter ceux qui restent.","Dessinent, barrent et comptent les objets restants.","Représenter l'action de retirer."],
    ["Abstraction / symbolisation","Relier l'action au signe − et à une écriture adaptée si cette symbolisation figure dans les acquis de la classe.","Associent la manipulation à la représentation symbolique proposée.","Comprendre le sens de la soustraction."],
    ["Objectivation et réinvestissement","Faire raconter la démarche et proposer un nouveau problème de retrait.","Expliquent puis résolvent une nouvelle situation.","Réinvestir l'idée de reste."]
   ], trace:"Soustraire, c'est retirer une quantité d'une collection et chercher ce qui reste.", exercise:"1. Prépare une collection.__EXERCISE_NL__2. Retire quelques objets.__EXERCISE_NL__3. Compte les objets restants et représente la situation.", correction:"Le nombre annoncé doit être celui des objets restant après le retrait. Adapter les quantités aux acquis du CI."
  },
  "Associer une quantité à une représentation":{
   objective:"Associer une petite collection d'objets à une représentation figurée ou chiffrée déjà étudiée.",
   prerequisite:"Dénombrer de petites collections et observer des dessins ou des symboles.",
   material:"Graines, jetons, cartes à points, cartes-nombres, images et ardoises.",
   situation:"L'enseignant présente plusieurs collections et plusieurs cartes à points. Les apprenants doivent retrouver la carte qui représente chaque collection.",
   stages:[
    ["Introduction","Présenter une collection et plusieurs cartes de représentations ; demander comment retrouver la carte correspondante.","Observent les objets et les cartes, puis proposent une association.","Comprendre qu'une même quantité peut être montrée de plusieurs façons."],
    ["Manipulation concrète","Faire dénombrer les objets puis rechercher la carte portant le même nombre de points.","Comptent les objets et associent la carte correspondante.","Associer correctement une collection et une représentation."],
    ["Représentation","Faire dessiner la collection ou placer des jetons sur une carte vierge.","Dessinent ou organisent les jetons pour représenter la quantité.","Passer de l'objet réel à une représentation figurée."],
    ["Abstraction / verbalisation","Présenter l'écriture chiffrée correspondante si elle a déjà été étudiée et faire verbaliser le lien entre les représentations.","Associent objets, points, dessins et chiffre connu.","Relier plusieurs représentations d'une même quantité."],
    ["Objectivation et réinvestissement","Proposer de nouvelles associations sans modèle immédiat.","Choisissent une représentation et expliquent leur choix.","Réinvestir l'association quantité-représentation de manière autonome."]
   ],
   trace:"Une quantité peut être représentée par des objets, des dessins, des points ou un chiffre déjà appris. Ces représentations correspondent à la même quantité.",
   exercise:"1. Compte les objets et relie-les à la carte à points correspondante.__EXERCISE_NL__2. Dessine une collection qui correspond à la carte proposée.__EXERCISE_NL__3. Associe la collection au chiffre étudié.",
   correction:"Chaque collection doit être reliée à une représentation de même quantité. N'utiliser que les chiffres déjà abordés dans la progression."
  },
  "Reconnaître et construire les nombres étudiés":{
   objective:"Construire une quantité demandée et reconnaître le nombre correspondant parmi les nombres déjà étudiés.",
   prerequisite:"Dénombrer et associer une collection à une représentation.",
   material:"Bâtonnets, graines, capsules, cartes-nombres, tableau et ardoises.",
   situation:"L'enseignant montre une carte-nombre connue et demande aux apprenants de préparer une collection qui représente cette quantité.",
   stages:[
    ["Introduction","Présenter une carte-nombre connue et demander comment fabriquer la collection correspondante.","Observent la carte et expliquent ce qu'ils doivent préparer.","Identifier la quantité demandée."],
    ["Manipulation concrète","Faire prendre les objets un à un jusqu'à obtenir la quantité demandée.","Constituent la collection et vérifient en comptant.","Construire une collection de quantité exacte."],
    ["Représentation","Faire représenter la collection par des points ou des dessins.","Dessinent ou marquent la quantité construite.","Représenter la quantité sans les objets réels."],
    ["Abstraction / verbalisation","Faire reconnaître la carte-nombre et associer le nom oral, la collection et le symbole connu.","Disent le nombre et montrent les différentes représentations correspondantes.","Relier quantité, nom oral et écriture chiffrée étudiée."],
    ["Objectivation et réinvestissement","Distribuer d'autres cartes-nombres connues et demander de construire les collections correspondantes.","Construisent et vérifient individuellement leurs collections.","Reconnaître et construire les nombres de la progression."]
   ],
   trace:"Pour construire un nombre, je prépare une collection qui contient exactement la quantité demandée. Je peux vérifier en comptant les objets un à un.",
   exercise:"1. Construis une collection correspondant à une carte-nombre connue.__EXERCISE_NL__2. Dessine cette collection.__EXERCISE_NL__3. Relie le dessin à la carte-nombre correspondante.",
   correction:"La collection doit contenir exactement le nombre d'éléments demandé. Adapter les cartes aux nombres déjà enseignés."
  },
  "Lire et écrire les nombres étudiés":{
   objective:"Lire oralement et écrire correctement les nombres déjà étudiés, en chiffres et selon les apprentissages prévus en lettres.",
   prerequisite:"Reconnaître les quantités et associer les collections aux écritures chiffrées.",
   material:"Cartes-nombres, étiquettes, tableau, ardoises, cahiers et matériel de manipulation.",
   situation:"Des cartes-nombres sont affichées au tableau. Les apprenants doivent les lire puis retrouver ou produire l'écriture demandée.",
   stages:[
    ["Introduction","Faire rappeler quelques nombres connus à partir de collections ou de cartes.","Observent, nomment les nombres et rappellent leurs acquis.","Mobiliser les nombres déjà rencontrés."],
    ["Manipulation et observation","Faire associer chaque carte-nombre à une collection correspondante.","Comptent les objets et choisissent la carte adaptée.","Comprendre le lien entre quantité et écriture du nombre."],
    ["Lecture guidée","Présenter les nombres de la séance et faire lire collectivement puis individuellement.","Prononcent les nombres et les distinguent visuellement.","Lire correctement les nombres étudiés."],
    ["Écriture","Montrer le tracé des chiffres et faire écrire sur ardoise ; travailler l'écriture en lettres uniquement si elle est prévue et acquise.","Tracent les chiffres puis vérifient leur production avec le modèle.","Écrire lisiblement les nombres de la séance."],
    ["Objectivation et évaluation","Dicter quelques nombres étudiés et faire associer lecture, écriture et quantité.","Lis­ent, écrivent et associent individuellement les nombres.","Montrer la maîtrise de la lecture et de l'écriture des nombres abordés."]
   ],
   trace:"Un nombre peut être lu et écrit. Son écriture chiffrée représente une quantité. Je m'entraîne à lire et à tracer les nombres étudiés en respectant leur forme.",
   exercise:"1. Lis les nombres présentés par le maître.__EXERCISE_NL__2. Écris sur ton ardoise les nombres dictés.__EXERCISE_NL__3. Relie chaque nombre à la collection correspondante.",
   correction:"Vérifier la lecture, le sens des chiffres et leur tracé. N'évaluer que les nombres effectivement enseignés."
  },
  "Ranger et comparer des nombres":{
   objective:"Comparer et ranger des nombres déjà étudiés en s'appuyant sur les collections, les représentations et les acquis de la classe.",
   prerequisite:"Lire les nombres étudiés et comparer des collections.",
   material:"Cartes-nombres, collections de jetons, bande numérique si disponible et ardoises.",
   situation:"Plusieurs cartes-nombres sont mélangées. Les apprenants doivent les organiser du plus petit au plus grand ou dans l'ordre inverse selon la consigne.",
   stages:[
    ["Introduction","Présenter deux collections puis leurs cartes-nombres et demander laquelle représente la plus grande quantité.","Comparent les collections et justifient leur choix.","Comprendre le sens de la comparaison des nombres."],
    ["Manipulation concrète","Faire constituer ou associer des collections aux nombres puis comparer les quantités.","Manipulent, dénombrent et comparent les collections.","S'appuyer sur les quantités pour comparer."],
    ["Représentation","Faire placer les cartes sur une bande numérique adaptée ou les organiser en ligne.","Positionnent et ordonnent les cartes selon la progression étudiée.","Représenter l'ordre des nombres."],
    ["Abstraction / verbalisation","Faire employer plus grand, plus petit, avant et après ; introduire les signes de comparaison seulement s'ils sont prévus dans les acquis.","Disent quel nombre est plus grand ou plus petit et expliquent l'ordre choisi.","Comparer et ranger les nombres avec le vocabulaire adapté."],
    ["Objectivation et réinvestissement","Proposer une nouvelle série de nombres à comparer et à ranger.","Rangent les nombres et vérifient leur travail.","Réinvestir la comparaison et le rangement des nombres connus."]
   ],
   trace:"Comparer des nombres permet de dire lequel est plus grand ou plus petit. Ranger des nombres, c'est les placer dans un ordre demandé.",
   exercise:"1. Compare deux nombres connus à partir de leurs collections.__EXERCISE_NL__2. Range trois cartes-nombres du plus petit au plus grand.__EXERCISE_NL__3. Range-les du plus grand au plus petit.",
   correction:"L'ordre doit respecter la valeur des nombres. Limiter les séries aux nombres étudiés et utiliser la manipulation si nécessaire."
  },
  "Décomposer et recomposer des nombres":{
   objective:"Décomposer une petite quantité en plusieurs parties et recomposer la quantité initiale par réunion des parties.",
   prerequisite:"Constituer, dénombrer et réunir de petites collections.",
   material:"Jetons de deux couleurs, graines, bâtonnets, boîtes compartimentées et cartes-nombres connues.",
   situation:"Une collection est partagée entre deux boîtes. Les apprenants cherchent combien d'objets se trouvent dans chaque boîte et combien il y en a en tout.",
   stages:[
    ["Introduction","Présenter une collection et deux récipients ; demander comment partager les objets sans en perdre.","Observent et proposent des façons de répartir les objets.","Comprendre qu'une quantité peut être partagée en parties."],
    ["Manipulation concrète","Faire répartir les objets en deux groupes, puis réunir les groupes pour retrouver la collection initiale.","Partagent, comptent chaque groupe et réunissent les parties.","Décomposer puis recomposer une quantité par manipulation."],
    ["Représentation","Faire dessiner les groupes avec des points ou des couleurs différentes.","Représentent les parties puis la collection réunie.","Montrer les parties et le tout par un dessin."],
    ["Abstraction / verbalisation","Faire expliquer qu'une même quantité peut être obtenue par différentes répartitions, sans imposer une écriture non étudiée.","Décrivent les différentes façons de partager et de recomposer.","Comprendre le lien entre les parties et le tout."],
    ["Objectivation et réinvestissement","Proposer une nouvelle collection à partager de plusieurs façons.","Effectuent une décomposition et vérifient en recomposant.","Réinvestir la décomposition et la recomposition des quantités connues."]
   ],
   trace:"Décomposer, c'est partager une quantité en plusieurs parties. Recomposer, c'est réunir les parties pour retrouver la quantité de départ.",
   exercise:"1. Partage une collection de jetons en deux groupes.__EXERCISE_NL__2. Compte les objets de chaque groupe.__EXERCISE_NL__3. Réunis les groupes et vérifie que tu retrouves la collection de départ.",
   correction:"La somme des parties doit correspondre à la collection initiale. Accepter plusieurs répartitions exactes et adaptées aux nombres étudiés."
  },
  "Résoudre de petits problèmes additifs":{
   objective:"Comprendre une situation-problème simple de réunion ou d'ajout, choisir une démarche et trouver le résultat par manipulation ou représentation.",
   prerequisite:"Comprendre les quantités, dénombrer et réunir de petites collections.",
   material:"Images, jetons, graines, objets familiers, cartes-nombres et ardoises.",
   situation:"Awa a quelques graines. Son camarade lui en donne encore. La classe doit trouver combien de graines Awa possède maintenant.",
   stages:[
    ["Compréhension de la situation","Raconter ou lire le problème lentement, faire observer l'image et demander ce que l'on sait et ce que l'on cherche.","Écoutent, reformulent et identifient les quantités et la question.","Comprendre la situation et repérer la question."],
    ["Recherche par manipulation","Faire représenter chaque quantité par des objets puis réunir les collections lorsque la situation le demande.","Préparent les collections, les réunissent et dénombrent le total.","Choisir une action adaptée à la situation."],
    ["Représentation","Faire dessiner les quantités et leur réunion ou utiliser des marques.","Dessinent les groupes et représentent le résultat.","Traduire la situation par un dessin ou un schéma simple."],
    ["Mise en commun et verbalisation","Inviter plusieurs apprenants à expliquer leur démarche ; relier la réunion à l'addition si elle a été étudiée.","Présentent leurs démarches et comparent les réponses.","Expliquer comment le résultat a été trouvé."],
    ["Évaluation et réinvestissement","Proposer un problème analogue avec d'autres objets et des nombres connus.","Résolvent individuellement le nouveau problème.","Réutiliser la démarche dans une situation nouvelle."]
   ],
   trace:"Pour résoudre un problème, j'écoute ou je lis l'énoncé, je cherche ce que l'on me demande, je représente la situation, je trouve la réponse et je vérifie.",
   exercise:"1. Maman a 2 mangues et en reçoit 1 autre. Combien a-t-elle de mangues ?__EXERCISE_NL__2. Représente le problème avec des dessins ou des jetons.__EXERCISE_NL__3. Explique comment tu as trouvé la réponse.",
   correction:"Exemple : 2 mangues réunies avec 1 mangue donnent 3 mangues. Accepter une résolution par manipulation, dessin ou écriture additive si celle-ci a déjà été enseignée. Adapter les nombres au niveau réel de la classe."
  }
 },
 "Géométrie":{
  "Se repérer dans l'espace : devant et derrière":{
   objective:"Identifier et employer correctement les positions devant et derrière dans des situations concrètes.", prerequisite:"Observer son environnement et suivre une consigne simple.", material:"Objets de la classe, élèves, jouets et images de scènes familières.",
   situation:"L'enseignant place un objet par rapport à un élève et demande de décrire sa position.",
   stages:[
    ["Introduction","Faire observer une disposition d'élèves ou d'objets et questionner leur position.","Observent et proposent des mots pour décrire la position.","Repérer la position relative de deux éléments."],
    ["Manipulation concrète","Faire placer un objet devant puis derrière un élève ou un autre objet.","Déplacent les objets et exécutent les consignes.","Exécuter correctement devant et derrière."],
    ["Représentation","Présenter ou faire dessiner des scènes montrant les deux positions.","Dessinent ou désignent les positions sur des images.","Associer les mots aux représentations."],
    ["Abstraction / verbalisation","Faire formuler des phrases décrivant la position.","Disent où se trouve l'objet en utilisant devant ou derrière.","Employer les termes spatiaux de façon correcte."],
    ["Objectivation et réinvestissement","Donner de nouvelles consignes de placement dans la classe.","Plaçent et décrivent les objets.","Réutiliser les notions dans un nouvel espace."]
   ], trace:"Devant et derrière indiquent la position d'un objet ou d'une personne par rapport à un repère.", exercise:"1. Place un objet devant ta chaise.__EXERCISE_NL__2. Place un objet derrière ta chaise.__EXERCISE_NL__3. Décris la position d'un objet dans une image.", correction:"L'objet doit être placé conformément au repère indiqué. La réponse orale doit utiliser le terme demandé."
  },
  "Reconnaître et reproduire un cercle":{
   objective:"Reconnaître un cercle parmi des formes proposées et en reproduire un avec un matériel adapté.", prerequisite:"Observer et comparer des formes simples.", material:"Objets ronds, couvercles, formes découpées, feuilles, crayons et gabarits.",
   situation:"L'enseignant présente plusieurs objets et formes ; les apprenants recherchent ceux qui ont une forme circulaire.",
   stages:[
    ["Introduction","Présenter des objets variés et demander lesquels ont une forme ronde.","Observent, touchent et proposent des réponses.","Repérer les objets présentant une forme circulaire."],
    ["Manipulation concrète","Faire trier des objets ou gabarits ronds et non ronds ; faire suivre leur contour.","Classent les formes et suivent le contour avec le doigt.","Identifier les caractéristiques visuelles du cercle."],
    ["Représentation","Faire reproduire un cercle en utilisant un gabarit ou un objet circulaire.","Tracent le contour et colorient ou reproduisent la forme.","Reproduire une forme circulaire reconnaissable."],
    ["Abstraction / verbalisation","Nommer la forme et la distinguer des autres formes présentées.","Désignent le cercle et le distinguent des autres formes.","Reconnaître et nommer le cercle."],
    ["Objectivation et réinvestissement","Faire rechercher dans la classe des objets ayant une forme circulaire.","Identifient et nomment des objets ronds.","Réinvestir la reconnaissance du cercle dans l'environnement."]
   ], trace:"Le cercle est une forme ronde. On peut reconnaître sa forme sur des objets et la reproduire à l'aide d'un gabarit.", exercise:"1. Entoure les formes qui sont des cercles.__EXERCISE_NL__2. Reproduis un cercle avec un gabarit.__EXERCISE_NL__3. Cite un objet de forme ronde.", correction:"Retenir les formes circulaires et vérifier que la reproduction est fermée et reconnaissable."
  },
  "Reconnaître et reproduire un carré":{
   objective:"Reconnaître un carré parmi des formes simples et en reproduire un à l'aide d'un modèle ou d'un gabarit.", prerequisite:"Observer, manipuler et comparer des formes.", material:"Formes découpées, carrés en carton, bâtonnets, feuilles et gabarits.",
   situation:"La classe reçoit des formes découpées et doit retrouver celles qui ressemblent au modèle carré présenté.",
   stages:[
    ["Introduction","Présenter un modèle carré parmi plusieurs formes.","Observent et recherchent la forme identique.","Identifier la forme à retrouver."],
    ["Manipulation concrète","Faire trier les carrés et comparer leurs côtés et leurs coins avec le modèle, sans exiger de vocabulaire non étudié.","Manipulent, superposent et classent les formes.","Reconnaître un carré par comparaison."],
    ["Représentation","Faire reproduire la forme par assemblage de bâtonnets ou à l'aide d'un gabarit.","Assemblent ou tracent un carré.","Reproduire une forme reconnaissable."],
    ["Abstraction / verbalisation","Faire nommer le carré et le distinguer des autres formes.","Désignent et nomment le carré.","Associer le nom à la forme."],
    ["Objectivation et réinvestissement","Faire rechercher des objets de forme carrée dans l'environnement.","Repèrent et décrivent des objets.","Réinvestir la reconnaissance du carré."]
   ], trace:"Le carré est une forme géométrique que l'on peut reconnaître, classer et reproduire à partir d'un modèle.", exercise:"1. Entoure les carrés parmi les formes proposées.__EXERCISE_NL__2. Reproduis un carré avec un gabarit ou des bâtonnets.__EXERCISE_NL__3. Recherche un objet de forme carrée.", correction:"L'apprenant doit identifier le carré et produire une forme correspondant au modèle."
  },
  "Reconnaître et reproduire un triangle":{
   objective:"Reconnaître un triangle parmi des formes proposées et en reproduire un à partir d'un modèle.", prerequisite:"Observer et comparer des formes simples.", material:"Triangles en carton, autres formes découpées, bâtonnets, feuilles et crayons.",
   situation:"L'enseignant présente plusieurs formes et demande de retrouver celle qui ressemble au modèle triangulaire.",
   stages:[
    ["Introduction","Présenter un triangle parmi d'autres formes et faire exprimer les observations.","Observent et désignent la forme recherchée.","Repérer le triangle parmi les autres formes."],
    ["Manipulation concrète","Faire trier les triangles et suivre leurs contours avec le doigt.","Manipulent, trient et comparent les formes.","Reconnaître le triangle par observation."],
    ["Représentation","Faire construire ou reproduire un triangle avec des bâtonnets ou un gabarit.","Assemblent les bâtonnets ou tracent la forme.","Reproduire un triangle reconnaissable."],
    ["Abstraction / verbalisation","Faire nommer le triangle et le distinguer des autres formes.","Nomment et montrent le triangle.","Associer le nom à la forme étudiée."],
    ["Objectivation et réinvestissement","Proposer un nouveau tri et une recherche d'objets ou motifs triangulaires.","Identifient les triangles dans de nouveaux supports.","Réinvestir la reconnaissance du triangle."]
   ], trace:"Le triangle est une forme géométrique que l'on apprend à reconnaître, à nommer et à reproduire.", exercise:"1. Montre les triangles parmi plusieurs formes.__EXERCISE_NL__2. Reproduis un triangle avec des bâtonnets.__EXERCISE_NL__3. Dessine un triangle.", correction:"La forme produite doit être fermée et présenter trois côtés."
  }
 ,
  "Se repérer dans l'espace : dessus et dessous":{
   objective:"Situer un objet par rapport à un repère en utilisant correctement dessus et dessous.", prerequisite:"Observer des objets et exécuter des consignes simples de placement.", material:"Table, chaise, boîte, cahiers, jouets et images de situations familières.",
   situation:"L'enseignant place un cahier sur une table puis un objet sous la table et demande aux apprenants de décrire les positions.",
   stages:[
    ["Introduction","Présenter deux objets placés l'un au-dessus ou au-dessous de l'autre et questionner leur position.","Observent et proposent des mots pour décrire les positions.","Repérer la position d'un objet par rapport à un autre."],
    ["Manipulation concrète","Faire placer successivement un objet dessus puis dessous un support clairement identifié.","Manipulent les objets et exécutent les consignes.","Exécuter correctement les consignes dessus et dessous."],
    ["Représentation","Présenter des images puis faire dessiner un objet placé dessus ou dessous un autre.","Désignent les positions et réalisent des dessins simples.","Associer chaque mot à une représentation correcte."],
    ["Abstraction / verbalisation","Faire décrire plusieurs dispositions en utilisant les mots dessus et dessous.","Formulent des phrases complètes avec les mots étudiés.","Employer correctement le vocabulaire spatial."],
    ["Objectivation et réinvestissement","Proposer de nouvelles situations avec le mobilier et les objets de la classe.","Placent les objets et expliquent leur position.","Réutiliser les repères dans un autre contexte."]
   ], trace:"Dessus et dessous indiquent la position d'un objet par rapport à un repère. Je peux dire : le livre est sur la table ; le sac est sous la table.", exercise:"1. Place un crayon sur ton cahier.__EXERCISE_NL__2. Place un objet sous ta chaise.__EXERCISE_NL__3. Décris la position de deux objets dans une image.", correction:"L'objet doit être placé conformément au repère. Vérifier l'emploi oral de dessus/sur et dessous/sous selon la consigne."
  },
  "Se repérer dans l'espace : entre et à côté":{
   objective:"Identifier et décrire la position d'un objet ou d'une personne entre deux repères ou à côté d'un repère.", prerequisite:"Repérer des positions simples dans l'espace et suivre une consigne.", material:"Élèves, chaises, boîtes, jouets et images de scènes.",
   situation:"L'enseignant place un objet entre deux boîtes puis un autre à côté d'une boîte et demande de décrire chaque position.",
   stages:[
    ["Introduction","Faire observer trois objets alignés puis deux objets voisins et demander de décrire leur disposition.","Observent et proposent des descriptions.","Comprendre les relations spatiales à étudier."],
    ["Manipulation concrète","Faire placer un objet entre deux autres, puis à côté d'un objet repère.","Déplacent les objets et réalisent les placements demandés.","Réaliser correctement les deux placements."],
    ["Représentation","Faire observer et compléter des images ou dessins montrant les positions.","Désignent, dessinent ou complètent les dispositions.","Représenter les positions entre et à côté."],
    ["Abstraction / verbalisation","Faire nommer les repères et construire des phrases décrivant les positions.","Utilisent les mots entre et à côté dans des phrases.","Employer le vocabulaire spatial avec précision."],
    ["Objectivation et réinvestissement","Donner de nouvelles consignes avec des objets de la classe.","Effectuent les placements et expliquent leur démarche.","Réinvestir les notions dans une situation nouvelle."]
   ], trace:"Un objet est entre deux autres lorsqu'il se trouve au milieu d'eux. Il est à côté d'un objet lorsqu'il est près de cet objet.", exercise:"1. Place un objet entre deux cahiers.__EXERCISE_NL__2. Place un crayon à côté de ta trousse.__EXERCISE_NL__3. Décris la position d'un élève dans un rang.", correction:"Vérifier que l'objet est situé entre les deux repères demandés ou près du repère désigné."
  },
  "Reconnaître et tracer des lignes":{
   objective:"Observer, reconnaître et tracer des lignes simples à main levée ou à l'aide d'un matériel adapté.", prerequisite:"Tenir correctement un crayon et réaliser des gestes graphiques simples.", material:"Ficelles, bandes, règles, feuilles, crayons, ardoises et tracés modèles.",
   situation:"L'enseignant montre une ficelle tendue, une ficelle courbée et différents tracés ; les apprenants cherchent à les distinguer et à les reproduire.",
   stages:[
    ["Introduction","Présenter des ficelles et des tracés variés ; demander ce qui est semblable ou différent.","Observent, décrivent et comparent les tracés.","Repérer visuellement différentes lignes."],
    ["Manipulation concrète","Faire tendre, courber et déplacer une ficelle ; faire suivre les tracés avec le doigt.","Manipulent les ficelles et suivent les lignes.","Percevoir le trajet et la forme d'une ligne."],
    ["Représentation","Faire reproduire des lignes simples sur ardoise ou feuille, d'abord librement puis à partir d'un modèle.","Tracent des lignes et comparent leur production au modèle.","Produire un tracé continu et reconnaissable."],
    ["Abstraction / verbalisation","Faire décrire les lignes observées avec des mots accessibles : droite, courbe, ouverte ou fermée selon les exemples étudiés.","Nomment et décrivent les tracés.","Associer un vocabulaire simple aux lignes observées."],
    ["Objectivation et réinvestissement","Proposer un tri de nouveaux tracés et demander d'en reproduire quelques-uns.","Classent et reproduisent les lignes.","Reconnaître et tracer des lignes dans une nouvelle tâche."]
   ], trace:"Une ligne est un tracé. Elle peut être droite ou courbe. On peut observer des lignes ouvertes ou fermées et apprendre à les reproduire.", exercise:"1. Suis du doigt trois lignes différentes.__EXERCISE_NL__2. Reproduis une ligne droite et une ligne courbe.__EXERCISE_NL__3. Entoure une ligne fermée parmi plusieurs tracés.", correction:"Les tracés doivent être continus et correspondre au modèle demandé. Ne demander que les distinctions effectivement travaillées pendant la séance."
  },
  "Classer et assembler des formes géométriques":{
   objective:"Trier des formes géométriques selon leur apparence puis assembler des formes pour réaliser une composition simple.", prerequisite:"Reconnaître quelques formes usuelles présentées en classe.", material:"Formes découpées en carton ou papier, carrés, triangles, cercles, grandes feuilles et colle si disponible.",
   situation:"La classe reçoit un ensemble de formes mélangées et doit les regrouper puis les utiliser pour composer une image simple.",
   stages:[
    ["Introduction","Présenter un lot de formes mélangées et demander comment les organiser.","Observent les formes et proposent des critères de classement.","Identifier des ressemblances et des différences."],
    ["Manipulation concrète","Faire trier les formes par ressemblance, puis proposer de les juxtaposer ou de les assembler.","Manipulent, regroupent et assemblent les formes.","Classer et combiner les formes selon une consigne."],
    ["Représentation","Faire réaliser une composition simple avec les formes classées et la faire reproduire sur une feuille.","Construisent une image ou un motif et le reproduisent.","Passer de la manipulation à une représentation."],
    ["Abstraction / verbalisation","Faire expliquer le critère de classement et nommer les formes déjà étudiées.","Décrivent les regroupements et nomment les formes connues.","Justifier un classement avec un vocabulaire adapté."],
    ["Objectivation et réinvestissement","Distribuer un nouveau lot de formes et demander un classement puis un assemblage différent.","Réalisent une nouvelle composition et expliquent leurs choix.","Réinvestir le tri et l'assemblage dans une tâche nouvelle."]
   ], trace:"On peut classer des formes en regroupant celles qui se ressemblent. On peut aussi les assembler pour créer une image ou un motif.", exercise:"1. Regroupe les formes qui se ressemblent.__EXERCISE_NL__2. Nomme les formes que tu connais.__EXERCISE_NL__3. Assemble des formes pour réaliser une maison ou un autre dessin.", correction:"Le classement doit suivre un critère visible et cohérent. La composition peut varier si les formes sont correctement utilisées."
  },
  "Reproduire un assemblage de formes":{
   objective:"Observer un modèle composé de plusieurs formes, repérer leur disposition et reproduire l'assemblage.", prerequisite:"Reconnaître et manipuler des formes simples ; se repérer dans une disposition spatiale.", material:"Modèles illustrés, formes découpées, feuilles, crayons et supports de manipulation.",
   situation:"L'enseignant présente une figure composée de formes simples et demande aux apprenants de la reconstruire avec des pièces séparées.",
   stages:[
    ["Introduction","Présenter un assemblage modèle et laisser les apprenants observer ses différentes parties.","Observent et décrivent les formes et leur disposition.","Repérer les éléments qui composent le modèle."],
    ["Manipulation concrète","Distribuer les formes nécessaires et guider l'observation de leur position et de leur orientation.","Choisissent les pièces et les placent pour reproduire le modèle.","Reconstituer l'assemblage par manipulation."],
    ["Représentation","Faire dessiner ou coller l'assemblage obtenu, puis comparer avec le modèle.","Reproduisent l'assemblage et vérifient les positions.","Représenter fidèlement une composition simple."],
    ["Abstraction / verbalisation","Faire expliquer les étapes : choisir les formes, les placer et vérifier leur disposition.","Décrivent leur démarche avec des mots simples.","Expliquer comment reproduire un modèle."],
    ["Objectivation et réinvestissement","Proposer un autre modèle adapté et demander une reproduction autonome.","Reproduisent le nouvel assemblage et contrôlent leur travail.","Transférer la démarche à un nouveau modèle."]
   ], trace:"Pour reproduire un assemblage, j'observe le modèle, je reconnais les formes, je les place comme sur le modèle et je vérifie le résultat.", exercise:"1. Observe un modèle composé de formes.__EXERCISE_NL__2. Reconstitue-le avec les pièces proposées.__EXERCISE_NL__3. Dessine ou colle ton assemblage.", correction:"L'assemblage attendu doit reprendre les formes et leur disposition générale. Accepter les différences de taille si elles ne sont pas l'objet de l'activité."
  }
 },
 "Mesures":{
  "Comparer des longueurs : long et court":{
   objective:"Comparer directement deux objets selon leur longueur et employer long et court.", prerequisite:"Observer et manipuler des objets de la vie courante.", material:"Ficelles, bandes de papier, crayons, bâtons et objets de longueurs différentes.",
   situation:"L'enseignant présente deux bandes et demande laquelle est longue et laquelle est courte.",
   stages:[
    ["Introduction","Présenter deux objets de longueurs différentes et poser une question de comparaison.","Observent et proposent une réponse.","Comprendre que l'on compare les longueurs."],
    ["Manipulation concrète","Faire aligner les objets à une même origine pour comparer leurs extrémités.","Manipulent, alignent et comparent les objets.","Comparer correctement deux longueurs."],
    ["Représentation","Faire dessiner ou classer les objets du plus court au plus long.","Dessinent ou classent les bandes.","Représenter le résultat de la comparaison."],
    ["Abstraction / verbalisation","Faire employer les mots long et court dans des phrases simples.","Décrivent les objets avec les mots étudiés.","Employer le vocabulaire de longueur."],
    ["Objectivation et réinvestissement","Faire comparer d'autres objets de la classe.","Comparent et justifient leur choix.","Réinvestir la comparaison des longueurs."]
   ], trace:"Pour comparer deux longueurs, je place les objets au même point de départ. Je peux dire qu'un objet est long ou court.", exercise:"1. Compare deux crayons.__EXERCISE_NL__2. Montre la bande la plus courte.__EXERCISE_NL__3. Classe trois bandes de la plus courte à la plus longue.", correction:"Les objets doivent être alignés au même point de départ avant la comparaison."
  },
  "Comparer des masses : lourd et léger":{
   objective:"Comparer la masse de deux objets par manipulation et employer lourd et léger.", prerequisite:"Manipuler des objets et exprimer une comparaison simple.", material:"Objets de masses différentes, balance à plateaux si disponible, sacs et boîtes.",
   situation:"L'enseignant présente deux objets et demande lequel semble le plus lourd.",
   stages:[
    ["Introduction","Présenter deux objets et demander comment comparer leur masse.","Observent et émettent des hypothèses.","Identifier ce qui doit être comparé."],
    ["Manipulation concrète","Faire soupeser les objets, puis utiliser une balance à plateaux si disponible.","Soupèsent et observent l'équilibre ou l'inclinaison de la balance.","Comparer la masse par une expérience simple."],
    ["Représentation","Faire associer les objets à des images ou dessins représentant lourd et léger.","Classent les dessins selon la comparaison réalisée.","Représenter la comparaison de masses."],
    ["Abstraction / verbalisation","Faire formuler des phrases avec lourd et léger.","Décrivent les objets en utilisant les mots étudiés.","Employer correctement le vocabulaire."],
    ["Objectivation et réinvestissement","Proposer une autre paire d'objets à comparer.","Comparent et expliquent leur réponse.","Réinvestir la comparaison de masses."]
   ], trace:"On peut comparer la masse de deux objets en les soupesant ou avec une balance. On emploie les mots lourd et léger.", exercise:"1. Compare deux objets en les soupesant.__EXERCISE_NL__2. Montre l'objet le plus lourd.__EXERCISE_NL__3. Emploie les mots lourd et léger dans deux phrases.", correction:"La réponse doit être cohérente avec la comparaison réelle ; ne pas confondre taille et masse."
  },
  "Comparer des contenances : plein et vide":{
   objective:"Distinguer un récipient plein d'un récipient vide ou contenant moins de liquide.", prerequisite:"Observer des récipients et suivre une consigne simple.", material:"Bouteilles transparentes, gobelets, eau, bassines et images.",
   situation:"L'enseignant montre des récipients contenant des quantités différentes d'eau et demande de les décrire.",
   stages:[
    ["Introduction","Présenter un récipient plein et un récipient vide ou presque vide.","Observent et décrivent ce qu'ils voient.","Identifier les différences de contenance visible."],
    ["Manipulation concrète","Faire remplir, vider et transvaser de petites quantités d'eau sous surveillance.","Manipulent les récipients et observent les niveaux.","Distinguer plein et vide par l'expérience."],
    ["Représentation","Faire associer les récipients réels à des dessins de récipients pleins et vides.","Classent les images et les décrivent.","Associer l'expérience à une représentation."],
    ["Abstraction / verbalisation","Faire utiliser les mots plein et vide, puis comparer des récipients contenant plus ou moins.","Formulent des phrases de comparaison.","Employer le vocabulaire de contenance étudié."],
    ["Objectivation et réinvestissement","Faire décrire des récipients dans une nouvelle situation.","Identifient et décrivent les contenances.","Réutiliser les mots étudiés dans la vie courante."]
   ], trace:"Un récipient peut être plein ou vide. On peut comparer ce que contiennent deux récipients en observant ou en transvasant leur contenu.", exercise:"1. Montre le récipient plein.__EXERCISE_NL__2. Montre le récipient vide.__EXERCISE_NL__3. Décris deux récipients contenant des quantités différentes.", correction:"Vérifier que l'apprenant distingue correctement les situations et utilise les mots étudiés."
  },
  "Se repérer dans le temps : matin, midi et soir":{
   objective:"Identifier des moments de la journée et les associer à des activités familières.", prerequisite:"Raconter une activité vécue et observer des images.", material:"Images d'activités quotidiennes, frise de la journée et cartes illustrées.",
   situation:"L'enseignant présente des images du réveil, du repas et du coucher et demande à quel moment elles correspondent.",
   stages:[
    ["Introduction","Faire raconter quelques activités quotidiennes des apprenants.","Évoquent des activités de la journée.","Mobiliser les repères temporels connus."],
    ["Manipulation / classement","Faire classer des images selon le matin, le midi et le soir.","Manipulent et classent les images.","Associer les activités aux moments correspondants."],
    ["Représentation","Construire une frise illustrée de la journée.","Plaçent les images dans l'ordre de la journée.","Représenter une succession de moments."],
    ["Abstraction / verbalisation","Faire nommer matin, midi et soir et formuler des phrases.","Nomment les moments et décrivent les activités.","Employer les repères temporels étudiés."],
    ["Objectivation et réinvestissement","Demander de raconter une journée en utilisant les mots étudiés.","Racontent une courte succession d'activités.","Réinvestir les repères dans une situation personnelle."]
   ], trace:"Dans la journée, on distingue notamment le matin, le midi et le soir. Certaines activités se déroulent à des moments habituels.", exercise:"1. Classe les images du matin, du midi et du soir.__EXERCISE_NL__2. Cite une activité du matin.__EXERCISE_NL__3. Raconte une activité du soir.", correction:"Les images sont classées selon le moment représenté ; accepter les variations d'habitudes familiales lorsqu'elles sont cohérentes."
  }
 }
};

// Banque CP : les intitulés ci-dessous sont attestés dans le Guide Mathématiques CP 2022 fourni.
// Les objectifs, étapes, exercices et corrections détaillés restent des propositions de mise en œuvre.
const MATH_CP = {
 "Arithmétique": {
  "Les nombres de 0 à 80 : comptage, lecture et écriture": {
   sourceStatus:"Notion attestée dans le guide de Mathématiques CP fourni",
   sourceDetail:"Le guide mentionne les nombres de 0 à 80. Les formulations de l’objectif et les étapes ci-dessous sont indicatives.",
   objective:"Compter, lire et écrire des nombres compris dans la plage travaillée en classe, en s’appuyant sur des collections et des représentations.",
   prerequisite:"Compter des collections et reconnaître les écritures numériques déjà étudiées.",
   material:"Bâtonnets, capsules, paquets de dix, cartes-nombres, ardoises et guide de Mathématiques CP.",
   situation:"L’enseignant présente des collections organisées et demande aux apprenants de les dénombrer, puis de faire correspondre quantité, représentation et écriture chiffrée.",
   stages:[
    ["Rappel et mise en situation","Présenter une collection et demander comment la dénombrer et écrire le nombre obtenu.","Observent, rappellent les acquis et proposent une démarche.","Mobiliser les acquis utiles à la lecture et à l’écriture des nombres."],
    ["Manipulation et comptage","Faire grouper, déplacer ou pointer les objets pour éviter les doubles comptages.","Manipulent et comptent les objets de façon organisée.","Déterminer correctement la quantité de la collection."],
    ["Représentation","Faire représenter les quantités par des dessins, des groupements ou des cartes adaptées.","Représentent les quantités et établissent des correspondances.","Relier la collection à une représentation."],
    ["Lecture et écriture","Présenter les écritures chiffrées correspondant aux nombres de la séance et guider leur lecture et leur écriture.","Lis­ent les nombres et les écrivent sur l’ardoise.","Lire et écrire les nombres effectivement étudiés."],
    ["Entraînement et vérification","Proposer de nouvelles collections et une courte dictée de nombres adaptés à la progression.","Réalisent les tâches individuellement puis corrigent.","Vérifier le comptage, la lecture et l’écriture des nombres." ]
   ],
   trace:"Pour lire et écrire un nombre, j’observe son écriture et je le relie à la quantité qu’il représente. Je m’exerce avec les nombres déjà étudiés en classe.",
   exercise:"1. Dénombre une collection préparée par l’enseignant.\n2. Relie chaque collection à la carte-nombre correspondante.\n3. Lis puis écris les nombres proposés par l’enseignant.",
   correction:"Les réponses doivent correspondre aux quantités réellement présentées. N’utiliser que les nombres travaillés dans la progression de la classe."
  },
  "Les nombres de 81 à 99 : comptage, lecture, écriture, comparaison et rangement": {
   sourceStatus:"Notion attestée dans le guide de Mathématiques CP fourni",
   sourceDetail:"Le guide mentionne les nombres de 81 à 99 ainsi que le comptage, le décomptage, la lecture, l’écriture, la comparaison et le rangement. Les étapes détaillées sont indicatives.",
   objective:"Dénombrer, lire, écrire, comparer et ranger des nombres de la plage étudiée à l’aide de matériel et de représentations.",
   prerequisite:"Maîtriser les nombres antérieurs et les groupements utilisés dans la classe.",
   material:"Bâtonnets, paquets de dix, capsules, cartes-nombres et ardoises.",
   situation:"Plusieurs cartes-nombres et collections sont présentées. Les apprenants doivent les lire, les associer aux quantités et les ranger.",
   stages:[
    ["Rappel et situation-problème","Faire rappeler les groupements et nombres déjà étudiés.","Rappellent les acquis et observent les supports.","Mobiliser les acquis numériques antérieurs."],
    ["Manipulation et groupements","Faire représenter les quantités avec des groupements adaptés et des unités restantes.","Constituent et dénombrent les collections.","Relier les groupements à la quantité représentée."],
    ["Lecture et écriture","Présenter les cartes-nombres et faire lire puis écrire les nombres ciblés.","Lis­ent les nombres et les écrivent sur l’ardoise.","Lire et écrire correctement les nombres étudiés."],
    ["Comparaison et rangement","Faire comparer les nombres avec du matériel, puis ranger quelques cartes dans l’ordre demandé.","Comparent et rangent les cartes-nombres.","Comparer et ranger les nombres sans se fier à leur seule apparence."],
    ["Évaluation et remédiation","Proposer une courte tâche individuelle de lecture, écriture, comparaison ou rangement.","Réalisent la tâche et corrigent avec l’enseignant.","Identifier les acquis et les difficultés à reprendre."]
   ],
   trace:"Je peux lire, écrire, comparer et ranger les nombres étudiés. Pour comparer, je m’appuie sur leur valeur et sur les représentations travaillées en classe.",
   exercise:"1. Lis les nombres présentés.\n2. Écris les nombres dictés.\n3. Compare puis range les cartes-nombres proposées.",
   correction:"Vérifier la lecture et l’écriture exactes ainsi que le sens du rangement demandé. Adapter les nombres aux apprentissages déjà réalisés."
  },
  "Les nombres de 0 à 80 : addition, soustraction et problèmes": {
   sourceStatus:"Notion attestée dans le guide de Mathématiques CP fourni",
   sourceDetail:"Le guide mentionne l’addition, la soustraction et la résolution de problèmes sur les nombres de 0 à 80. Les exemples et les étapes sont indicatifs.",
   objective:"Résoudre des situations simples d’addition ou de soustraction avec des nombres adaptés aux apprentissages réalisés.",
   prerequisite:"Dénombrer, comparer des quantités et comprendre les actions de réunion et de retrait.",
   material:"Jetons, bâtonnets, capsules, dessins, cartes-nombres et ardoises.",
   situation:"Une courte histoire présente des objets que l’on réunit ou dont on retire une partie. Les apprenants cherchent la quantité totale ou restante.",
   stages:[
    ["Compréhension du problème","Lire ou raconter la situation, faire identifier les données et la question.","Écoutent, reformulent et disent ce qu’il faut chercher.","Identifier la question et les informations utiles."],
    ["Résolution par manipulation","Faire représenter l’histoire avec des objets et exécuter l’action de réunion ou de retrait.","Manipulent et dénombrent le résultat.","Trouver une réponse par une action concrète."],
    ["Représentation","Faire dessiner les quantités et les actions effectuées.","Dessinent et expliquent leur représentation.","Relier l’action à une représentation compréhensible."],
    ["Calcul et verbalisation","Guider l’écriture du calcul seulement selon les procédures étudiées et faire expliquer le choix.","Effectuent le calcul adapté et expliquent leur démarche.","Choisir une opération pertinente et trouver le résultat."],
    ["Réinvestissement","Proposer un problème analogue avec des nombres adaptés.","Résolvent individuellement puis vérifient la réponse.","Réutiliser la démarche dans une nouvelle situation."]
   ],
   trace:"Dans un problème, je comprends l’histoire, je repère ce qu’on cherche, je représente la situation, puis je calcule et je vérifie ma réponse.",
   exercise:"1. Résous une situation où deux petites quantités sont réunies.\n2. Résous une situation où l’on retire une quantité.\n3. Explique comment tu as trouvé la réponse.",
   correction:"La procédure doit correspondre à la situation. Vérifier la réponse par manipulation ou représentation et n’utiliser que les calculs étudiés."
  },
  "Les nombres de 0 à 99 : addition, soustraction et problèmes": {
   sourceStatus:"Notion attestée dans le guide de Mathématiques CP fourni",
   sourceDetail:"Le guide mentionne les opérations et la résolution de problèmes sur les nombres de 0 à 99. Les procédures détaillées sont indicatives et doivent suivre la progression de la classe.",
   objective:"Résoudre des exercices et problèmes d’addition ou de soustraction dans la plage numérique étudiée.",
   prerequisite:"Lire et écrire les nombres utilisés et comprendre les situations de réunion et de retrait.",
   material:"Cartes-nombres, matériel de numération, ardoises et cahiers d’activités.",
   situation:"Les apprenants comparent plusieurs situations de réunion ou de retrait et choisissent une démarche adaptée.",
   stages:[
    ["Mise en situation","Présenter une situation-problème et faire préciser la question.","Reformulent la situation et identifient ce qu’il faut trouver.","Comprendre la situation et la question."],
    ["Recherche","Laisser les apprenants essayer avec le matériel ou les représentations connues.","Manipulent, dessinent et proposent une procédure.","Proposer une démarche de résolution."],
    ["Mise en commun","Faire comparer les démarches et vérifier les résultats.","Présentent et justifient leurs réponses.","Expliquer une démarche correcte."],
    ["Structuration","Faire rappeler les étapes de résolution et les procédures déjà étudiées.","Formulent les étapes et prennent la trace écrite.","Retenir une méthode adaptée à la situation."],
    ["Application et remédiation","Proposer une tâche individuelle et reprendre les erreurs avec du matériel si nécessaire.","Résolvent puis corrigent leur travail.","Réinvestir et consolider les acquis."]
   ],
   trace:"Pour résoudre un problème, je lis ou j’écoute l’énoncé, je cherche ce qu’on demande, je choisis une démarche, je calcule et je vérifie le résultat.",
   exercise:"1. Résous un problème d’addition avec des nombres étudiés.\n2. Résous un problème de soustraction.\n3. Explique ou représente ta démarche.",
   correction:"Les réponses dépendent des données des problèmes proposés. La démarche doit être cohérente et le résultat vérifié."
  },
  "Le nombre 100 : composition, représentation, identification, lecture et écriture": {
   sourceStatus:"Notion attestée dans le guide de Mathématiques CP fourni",
   sourceDetail:"Le guide mentionne le nombre 100 et les activités de composition, représentation, identification, lecture et écriture. Les propositions ci-dessous doivent être ajustées à la fiche du guide utilisée.",
   objective:"Identifier, représenter, lire et écrire le nombre 100 et comprendre sa composition à l’aide du matériel étudié.",
   prerequisite:"Manipuler des groupements de dix et connaître les nombres antérieurs travaillés.",
   material:"Bâtonnets groupés par dizaines, capsules, cartes-nombres, ardoises et cahier d’activités.",
   situation:"L’enseignant propose des groupements et demande aux apprenants comment représenter une quantité de cent unités.",
   stages:[
    ["Rappel","Faire représenter des groupements déjà étudiés et rappeler leur valeur.","Manipulent et rappellent les acquis.","Réactiver les connaissances nécessaires."],
    ["Construction concrète","Faire construire la quantité à l’aide de groupements de dix selon le matériel disponible.","Composent la quantité et comptent les groupements.","Relier les groupements à la quantité totale."],
    ["Représentation et identification","Présenter une représentation de 100 et faire identifier ce qu’elle signifie.","Associent le matériel, le dessin et le nombre.","Reconnaître la représentation de 100."],
    ["Lecture et écriture","Faire lire le nombre 100 et le faire écrire sur l’ardoise.","Lis­ent et écrivent 100.","Lire et écrire correctement le nombre étudié."],
    ["Application","Proposer une nouvelle représentation et demander d’identifier le nombre correspondant.","Réalisent la tâche puis vérifient.","Réinvestir la reconnaissance et l’écriture de 100."]
   ],
   trace:"Le nombre 100 s’écrit avec les chiffres 1, 0 et 0. Je peux le représenter à l’aide de groupements adaptés et le lire « cent ».",
   exercise:"1. Lis le nombre 100.\n2. Représente 100 à l’aide du matériel proposé.\n3. Écris le nombre dicté par l’enseignant lorsqu’il s’agit de cent.",
   correction:"La représentation doit correspondre à 100 unités selon le matériel utilisé. Vérifier la lecture et l’écriture de 100."
  }
 },
 "Géométrie": {
  "Le cube : faces planes, sommets et arêtes": {
   sourceStatus:"Notion attestée dans le guide de Mathématiques CP fourni",
   sourceDetail:"Le guide mentionne le cube et l’identification de ses faces planes, sommets et arêtes. Les activités détaillées ci-dessous sont indicatives.",
   objective:"Identifier un cube et observer ses faces, ses sommets et ses arêtes à partir d’un solide concret.",
   prerequisite:"Observer, manipuler et décrire des objets de l’environnement.",
   material:"Boîtes cubiques, cubes, objets de forme cubique, images et ardoises.",
   situation:"L’enseignant présente plusieurs solides ou objets et demande aux apprenants de repérer ceux qui ont la forme d’un cube.",
   stages:[
    ["Observation et découverte","Présenter différents objets et faire décrire leurs formes.","Observent, manipulent et proposent des classements.","Repérer le solide qui a la forme d’un cube."],
    ["Manipulation du cube","Faire toucher les surfaces, les arêtes et les sommets du cube.","Manipulent et montrent les éléments demandés.","Distinguer faces, arêtes et sommets par observation."],
    ["Description et représentation","Faire décrire le cube et observer une représentation ou une empreinte d’une face.","Décrivent le solide et reproduisent une représentation simple.","Décrire les caractéristiques visibles du cube."],
    ["Structuration","Faire reprendre le vocabulaire travaillé avec un modèle concret.","Nomment les éléments montrés.","Employer correctement les mots étudiés."],
    ["Application","Faire identifier un cube parmi plusieurs objets et montrer les éléments demandés.","Réalisent individuellement la tâche.","Vérifier l’identification et le vocabulaire géométrique."]
   ],
   trace:"Un cube est un solide. On peut observer ses faces planes, ses arêtes et ses sommets en manipulant un modèle.",
   exercise:"1. Choisis un objet qui a la forme d’un cube.\n2. Montre une face, une arête et un sommet sur le modèle.\n3. Décris le cube avec les mots étudiés.",
   correction:"L’apprenant doit désigner les éléments corrects sur un modèle concret. Le vocabulaire et les attentes exactes sont à ajuster au guide de la classe."
  },
  "Résolution de problèmes en géométrie": {
   sourceStatus:"Thème d’intégration attesté dans le guide de Mathématiques CP fourni",
   sourceDetail:"Le guide mentionne des situations d’intégration en géométrie. Les problèmes proposés et les étapes sont des exemples indicatifs.",
   objective:"Mobiliser les connaissances géométriques déjà étudiées pour résoudre une situation simple.",
   prerequisite:"Reconnaître et manipuler les formes ou solides déjà étudiés.",
   material:"Formes découpées, solides, bâtonnets, images et matériel disponible dans la classe.",
   situation:"Une image ou une construction à compléter nécessite de reconnaître, choisir ou assembler des formes étudiées.",
   stages:[
    ["Compréhension","Présenter le problème et faire identifier la tâche demandée.","Observent, reformulent et repèrent les éléments utiles.","Comprendre le problème géométrique."],
    ["Recherche et manipulation","Laisser essayer avec les formes, les solides ou les bâtonnets.","Manipulent, comparent et proposent une solution.","Mobiliser les notions géométriques connues."],
    ["Mise en commun","Faire présenter et comparer les solutions.","Expliquent leur démarche et écoutent les autres.","Justifier un choix ou un assemblage."],
    ["Validation","Faire vérifier la solution à partir du modèle ou de la consigne.","Vérifient et corrigent si nécessaire.","S’assurer que la solution répond à la consigne."],
    ["Réinvestissement","Proposer un problème analogue adapté aux formes déjà étudiées.","Résolvent individuellement.","Réutiliser les acquis dans une autre situation."]
   ],
   trace:"Pour résoudre un problème géométrique, j’observe la situation, je choisis les formes ou les outils adaptés, je réalise la tâche et je vérifie le résultat.",
   exercise:"1. Observe une figure ou un assemblage.\n2. Reproduis ou complète le modèle avec le matériel disponible.\n3. Explique comment tu as vérifié ton résultat.",
   correction:"La réponse doit respecter la consigne et les propriétés des formes effectivement étudiées. Laisser plusieurs solutions possibles si la consigne le permet."
  }
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
 if($("classe").value==="CI" && disc==="Mathématiques" && MATH_CI[domain]){
   // Ne garder que les notions effectivement détaillées dans la banque CI.
   items=items.filter(x=>Boolean(MATH_CI[domain][x]));
 }
 if($("classe").value==="CP" && disc==="Mathématiques" && MATH_CP[domain]){
   items=Object.keys(MATH_CP[domain]);
 }
 items.forEach(x=>s.add(new Option(x,x)));
 if([...s.options].some(x=>x.value===old))s.value=old;
 updateSourceNotice();
}
function updateSourceNotice(){
 const classe=$("classe").value, disc=$("disc").value, domain=$("dom").value;
 const isFR=classe==="CI" && disc==="Français" && domain==="Lecture et sons";
 const isMathCI=classe==="CI" && disc==="Mathématiques";
 const isMathCP=classe==="CP" && disc==="Mathématiques" && Boolean(MATH_CP[domain]);
 $("sourceWarning").textContent=isFR
 ? "Base adaptée aux leçons A, L, T, O et P relevées dans le Guide pédagogique du manuel Réussir en français au CI (LAHA Éditions, 2024). Les activités sont reformulées ; vérifier les exemples dans le manuel."
 : isMathCI
 ? "Mathématiques CI : propositions pédagogiques indicatives. Vérifier l'ordre des notions, les nombres abordés et les formulations dans le guide de la classe."
 : isMathCP
 ? "Mathématiques CP : les thèmes de cette liste sont attestés dans le Guide Mathématiques CP 2022 fourni. Les objectifs, étapes, exercices et corrections générés sont des propositions de mise en œuvre, à confronter aux fiches du guide."
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
 return `<section class="fiche-section"><h3>${title}</h3><p>${escapeHTML(String(content||"À compléter selon la séance.").replace(/__EXERCISE_NL__/g,"\n"))}</p></section>`;
}
function generate(){
 const classe=$("classe").value, disc=$("disc").value, domain=$("dom").value, notion=$("notion").value;
 const type=$("type").value, total=Math.max(10,Number($("duree").value)||30);
 const special=(classe==="CI"&&disc==="Français"&&FR_CI[notion])?FR_CI[notion]:null;
 const cpMathLesson=(classe==="CP"&&disc==="Mathématiques"&&MATH_CP[domain])?MATH_CP[domain][notion]:null;
 let objective=$("objectif").value.trim()||(special?special.objective:(cpMathLesson?cpMathLesson.objective:`À la fin de la séance, l'apprenant sera capable de traiter correctement la notion : ${notion}.`));
 let competence=$("competence").value.trim()||(special?special.competence:(cpMathLesson?`Mobiliser les connaissances et démarches mathématiques nécessaires pour traiter une tâche liée à ${notion}.`:`Mobiliser les ressources nécessaires pour réaliser une tâche liée à ${notion}.`));
 let prerequisite=$("prerequis").value.trim()||(special?special.prerequisite:(cpMathLesson?cpMathLesson.prerequisite:"Acquis antérieurs en rapport avec la notion."));
 let material=$("materiel").value.trim()||(special?special.material:(cpMathLesson?cpMathLesson.material:"Tableau, ardoises, cahiers, matériel concret et supports adaptés à la notion."));
 const mathLesson=(classe==="CI" && disc==="Mathématiques" && MATH_CI[domain])?MATH_CI[domain][notion]:null;
 if(cpMathLesson){
  objective=$("objectif").value.trim()||cpMathLesson.objective;
  competence=$("competence").value.trim()||`Mobiliser les connaissances et démarches mathématiques nécessaires pour traiter une tâche liée à ${notion}.`;
  prerequisite=$("prerequis").value.trim()||cpMathLesson.prerequisite;
  material=$("materiel").value.trim()||cpMathLesson.material;
 }
 if(mathLesson){
  objective=$("objectif").value.trim()||mathLesson.objective;
  competence=$("competence").value.trim()||`Résoudre une situation simple liée à ${notion} en mobilisant la manipulation, la représentation et la verbalisation.`;
  prerequisite=$("prerequis").value.trim()||mathLesson.prerequisite;
  material=$("materiel").value.trim()||mathLesson.material;
 }
 let stages=special?special.stages:(mathLesson?mathLesson.stages:getGenericStages());
 let title=special?special.title:notion;
 let warning=special?`<div class="warning">${escapeHTML(special.caution||"Activités reformulées à partir des objectifs et étapes du guide pédagogique. Vérifier les exemples dans le manuel.")}</div>`:(mathLesson?`<div class="warning">Proposition pédagogique indicative pour le CI. Vérifier la place de cette notion dans la progression et les nombres effectivement étudiés à l'aide du guide de Mathématiques du CI.</div>`:"<div class=\"warning\">Proposition pédagogique indicative : adapter les phases, les contenus et les évaluations au programme officiel, au guide de l'enseignant et au niveau réel des apprenants.</div>");
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
  <div class="info" style="grid-column:1/-1"><strong>Situation de départ / situation-problème</strong>${escapeHTML($("situation").value.trim()||(mathLesson?mathLesson.situation:"L'enseignant présente une situation adaptée à l'environnement des apprenants et en lien avec la notion."))}</div>
 </div>`;
 const isOnlyResume=type==="resume", onlyExercises=type==="exercices";
 if(!isOnlyResume&&!onlyExercises){
  out+=`<div class="fiche-section"><h3>Déroulement de la séance</h3>${renderTable(stages,total)}</div>`;
 }
 const trace=special?special.trace:(cpMathLesson?cpMathLesson.trace:(mathLesson?mathLesson.trace:`À retenir : ${notion} — retenir la notion, la démarche ou la règle construite pendant la séance.`));
 const ex=special?special.exercise:(cpMathLesson?cpMathLesson.exercise:(mathLesson?mathLesson.exercise:`1. Proposer une tâche simple de reconnaissance ou d'application de « ${notion} ».
2. Réaliser un exercice d'application adapté au niveau.
3. Expliquer la démarche utilisée.`));
 const corr=special?special.correction:(cpMathLesson?cpMathLesson.correction:(mathLesson?mathLesson.correction:"Correction attendue : réponses exactes, démarche compréhensible et justification adaptée au niveau."));
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
 $("type").value="fiche";$("classe").value="CP";$("disc").value="Français";populateDomains();
 $("fiche").innerHTML='<p class="empty">Votre fiche pédagogique apparaîtra ici après avoir appuyé sur « Générer la fiche ».</p>';
}
$("disc").addEventListener("change",populateDomains);
$("dom").addEventListener("change",populateNotions);
$("classe").addEventListener("change",()=>{populateDomains();});
$("generate").addEventListener("click",generate);
$("copy").addEventListener("click",copyDocument);
$("print").addEventListener("click",()=>window.print());
$("reset").addEventListener("click",resetForm);
populateDomains();
</script>
</body>
</html>
