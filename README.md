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
header{background:var(--vert);color:white;padding:22px 14px;text-align:center}
header h1{margin:0;font-size:24px}
header p{margin:7px 0 0}
main{max-width:950px;margin:20px auto;padding:0 12px}
.card{background:white;border-radius:10px;padding:18px;margin-bottom:18px;box-shadow:0 2px 8px #00000010}
h2{color:var(--vert);font-size:20px;margin-top:0}
h3{color:var(--vert);font-size:17px}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:12px}
label{font-weight:bold;display:block;margin-bottom:4px}
input,select,textarea{width:100%;padding:10px;border:1px solid #b7c8bb;border-radius:6px;font:inherit;background:white}
textarea{min-height:78px;resize:vertical}
.field{margin-bottom:12px}
button{border:0;border-radius:6px;padding:12px 16px;background:var(--vert);color:white;font-weight:bold;font-size:15px;cursor:pointer;margin:5px 4px 5px 0}
button.secondary{background:#52665a}
.actions{margin:14px 0}
#fiche{display:none}
.meta p{margin:5px 0}
table{border-collapse:collapse;width:100%;background:white}
th,td{border:1px solid #65756a;padding:8px;vertical-align:top;text-align:left}
th{background:#e2eee5}
.small{font-size:13px;color:#52665a}
@media(max-width:650px){table{font-size:12px}th,td{padding:5px}}
@media print{
body{background:white;color:black;font-size:10pt}
header{background:white;color:black;padding:5px}
main{max-width:none;margin:0;padding:0}
.no-print,#formulaire{display:none!important}
#fiche{display:block!important}
.card{box-shadow:none;padding:0;margin:0}
table{font-size:8pt;page-break-inside:auto}
tr{page-break-inside:avoid}
th,td{padding:5px}
@page{size:A4 landscape;margin:10mm}
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
<p class="small">Remplis les champs utiles. Les suggestions automatiques sont des aides à adapter à la leçon réelle.</p>

<form id="form">
<div class="grid">
<div class="field"><label for="ecole">École</label><input id="ecole" placeholder="Nom de l'école"></div>
<div class="field"><label for="enseignant">Enseignant(e)</label><input id="enseignant" placeholder="Nom de l'enseignant(e)"></div>
<div class="field"><label for="classe">Classe *</label>
<select id="classe" required>
<option value="">Choisir</option><option>CI</option><option>CP</option><option>CE1</option><option>CE2</option><option>CM1</option><option>CM2</option>
</select></div>
<div class="field"><label for="discipline">Discipline *</label>
<select id="discipline" required>
<option value="">Choisir</option><option>Français</option><option>Mathématiques</option><option>Éducation sociale</option><option>EST</option><option>Éducation artistique</option><option>EPS</option>
</select></div>
<div class="field"><label for="sousDiscipline">Sous-discipline / domaine</label><input id="sousDiscipline" placeholder="Ex. : Arithmétique, Chant, Civisme"></div>
<div class="field"><label for="typeDoc">Type de document *</label>
<select id="typeDoc" required><option>Fiche de préparation complète</option><option>Résumé de cours</option></select></div>
<div class="field"><label for="date">Date</label><input id="date" type="date"></div>
<div class="field"><label for="periode">Période / semaine</label><input id="periode" placeholder="Ex. : 2e période, semaine 3"></div>
<div class="field"><label for="duree">Durée (minutes) *</label><input id="duree" type="number" min="5" value="30" required></div>
<div class="field"><label for="notion">Titre de la leçon / notion *</label><input id="notion" required placeholder="Ex. : Les diphtongues"></div>
</div>

<h3>Objectifs et prérequis</h3>
<div class="field"><label for="competence">Compétence(s) visée(s)</label><textarea id="competence" placeholder="Compétence disciplinaire et transversale"></textarea></div>
<div class="field"><label for="prerequis">Prérequis / acquis antérieurs</label><textarea id="prerequis" placeholder="Ce que les apprenants savent déjà"></textarea></div>
<div class="field"><label for="objectif">Objectif spécifique / résultats d'apprentissage visés</label><textarea id="objectif" placeholder="À la fin de la séance, l'apprenant sera capable de..."></textarea></div>

<h3>Préparation de la séance</h3>
<div class="field"><label for="materiel">Matériel et supports</label><textarea id="materiel" placeholder="Manuels, tableau, images, objets, ardoises..."></textarea></div>
<div class="field"><label for="situation">Situation de départ / situation-problème</label><textarea id="situation" placeholder="Situation concrète qui déclenche l'apprentissage"></textarea></div>
<div class="field"><label for="motivation">Motivation / consigne de départ</label><textarea id="motivation"></textarea></div>
<div class="field"><label for="decouverte">Découverte / recherche</label><textarea id="decouverte" placeholder="Activité proposée et consignes"></textarea></div>
<div class="field"><label for="construction">Construction / structuration des savoirs</label><textarea id="construction" placeholder="Démarche, explication, règles ou notions à retenir"></textarea></div>
<div class="field"><label for="application">Application / entraînement</label><textarea id="application" placeholder="Exercices ou tâches à réaliser"></textarea></div>
<div class="field"><label for="evaluation">Évaluation : tâche et critères de réussite</label><textarea id="evaluation" placeholder="Exercice, question ou production permettant de vérifier les acquis"></textarea></div>
<div class="field"><label for="remediation">Remédiation prévue</label><textarea id="remediation" placeholder="Aide prévue pour les apprenants en difficulté"></textarea></div>
<div class="field"><label for="prolongement">Objectivation / prolongement</label><textarea id="prolongement" placeholder="Ce que l'apprenant retient et réinvestissement"></textarea></div>
<div class="field"><label for="resume">Résumé ou trace écrite à retenir</label><textarea id="resume" placeholder="Définition, règle, méthode, exemple ou synthèse"></textarea></div>

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
const $ = id => document.getElementById(id);
const champs = [
"ecole","enseignant","classe","discipline","sousDiscipline","typeDoc",
"date","periode","duree","notion","competence","prerequis","objectif",
"materiel","situation","motivation","decouverte","construction",
"application","evaluation","remediation","prolongement","resume"
];

function valeur(id){
 return $(id).value.trim();
}
function echapper(texte){
 return texte.replace(/[&<>"']/g, c => ({
 "&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"
 })[c]);
}
function afficher(texte){
 return echapper(texte || "À compléter");
}
function ligne(label,id){
 return `<p><strong>${label} :</strong> ${afficher(valeur(id))}</p>`;
}
function durees(total){
 const pourcentages=[10,15,20,20,15,15,5];
 let result=pourcentages.map(p=>Math.floor(total*p/100));
 let reste=total-result.reduce((a,b)=>a+b,0);
 for(let i=0;i<reste;i++) result[i%result.length]++;
 return result;
}
function creerLigne(phase,minutes,consigne,activite,resultat,evaluation){
 return `<tr>
 <td><strong>${phase}</strong><br>${minutes} min</td>
 <td>${afficher(consigne)}</td>
 <td>${afficher(activite)}</td>
 <td>${afficher(resultat)}</td>
 <td>${afficher(evaluation)}</td>
 </tr>`;
}
function suggestions(){
 const discipline=valeur("discipline");
 const notion=valeur("notion");
 const classe=valeur("classe");
 const contexte=`la notion « ${notion} » en ${discipline}, classe ${classe}`;
 return {
 motivation: `Présenter une situation simple liée à ${contexte}. Poser une question qui suscite la curiosité.`,
 decouverte: `Faire observer, manipuler, lire ou résoudre une tâche liée à ${contexte}. Demander aux apprenants d'expliquer leurs démarches.`,
 construction: `Faire comparer les réponses, corriger les erreurs et formuler avec la classe la règle ou les connaissances essentielles.`,
 application: `Proposer des exercices progressifs sur ${notion}. Laisser les apprenants travailler individuellement ou en petits groupes.`,
 evaluation: `Demander une tâche individuelle permettant de vérifier si l'apprenant maîtrise ${notion}. Préciser les critères de réussite.`,
 resume: `Notion : ${notion}.\nDéfinition, règle ou méthode : à compléter selon le contenu du cours.\nExemple : à préparer en fonction du niveau ${classe}.`
 };
}
function generer(e){
 e.preventDefault();
 const total=Math.max(5,Number(valeur("duree"))||30);
 const type=valeur("typeDoc");
 const sug=suggestions();
 const motivation=valeur("motivation")||sug.motivation;
 const decouverte=valeur("decouverte")||sug.decouverte;
 const construction=valeur("construction")||sug.construction;
 const application=valeur("application")||sug.application;
 const evaluation=valeur("evaluation")||sug.evaluation;
 const resume=valeur("resume")||sug.resume;
 let html=`<h2>${afficher(type)} : ${afficher(valeur("notion"))}</h2>
 <div class="meta">
 ${ligne("École","ecole")}${ligne("Enseignant(e)","enseignant")}
 ${ligne("Classe","classe")}${ligne("Discipline","discipline")}
 ${ligne("Sous-discipline / domaine","sousDiscipline")}
 ${ligne("Date","date")}${ligne("Période / semaine","periode")}
 ${ligne("Durée","duree")}
 </div>
 <hr>
 ${ligne("Compétences visées","competence")}
 ${ligne("Prérequis","prerequis")}
 ${ligne("Objectif spécifique","objectif")}
 ${ligne("Matériel et supports","materiel")}`;
 if(type==="Résumé de cours"){
 html+=`<h3>Situation de départ</h3><p>${afficher(valeur("situation"))}</p>
 <h3>Leçon à retenir</h3><p style="white-space:pre-wrap">${afficher(resume)}</p>
 <h3>Exercices d'application</h3><p style="white-space:pre-wrap">${afficher(valeur("application")||sug.application)}</p>
 <h3>Vérification des acquis</h3><p style="white-space:pre-wrap">${afficher(evaluation)}</p>
 <h3>Remédiation</h3><p style="white-space:pre-wrap">${afficher(valeur("remediation"))}</p>`;
 }else{
 const d=durees(total);
 html+=`<h3>Déroulement de la séance</h3>
 <table><thead><tr><th>Phases / durée</th><th>Consignes et activités de l'enseignant</th><th>Activités des apprenants</th><th>Résultats attendus</th><th>Évaluation / observation</th></tr></thead><tbody>`;
 html+=creerLigne("1. Motivation / préparation",d[0],motivation,"Écoutent, observent et réagissent.","Les apprenants s'intéressent à la situation proposée.","Participation et réactions.");
 html+=creerLigne("2. Mise en situation / acquis antérieurs",d[1],valeur("situation")||"Présenter la situation-problème et rappeler les acquis utiles.","Rappellent leurs connaissances et comprennent la tâche.","La situation et le problème sont compris.","Questions orales.");
 html+=creerLigne("3. Découverte / recherche",d[2],decouverte,"Observent, recherchent, manipulent et proposent des réponses.","Des pistes de solution ou premières observations sont formulées.","Pertinence des démarches.");
 html+=creerLigne("4. Construction / structuration",d[3],construction,"Comparent, justifient, corrigent et formulent la règle.","Les notions essentielles sont formulées et comprises.","Vérification des réponses et reformulation.");
 html+=creerLigne("5. Application / entraînement",d[4],application,"Résolvent les exercices seuls ou en groupe.","Les apprenants appliquent les connaissances étudiées.","Correction des productions.");
 html+=creerLigne("6. Évaluation",d[5],evaluation,"Réalisent individuellement la tâche demandée.","Les acquis sont vérifiés au regard de l'objectif.","Résultats selon les critères de réussite.");
 html+=creerLigne("7. Objectivation / prolongement",d[6],valeur("prolongement")||"Faire rappeler l'essentiel et proposer un réinvestissement.","Résument ce qu'ils ont appris et indiquent ce qu'ils retiennent.","L'essentiel de la leçon est retenu.","Synthèse orale ou trace écrite.");
 html+=`</tbody></table>
 <h3>Trace écrite / résumé</h3><p style="white-space:pre-wrap">${afficher(resume)}</p>
 <h3>Remédiation</h3><p style="white-space:pre-wrap">${afficher(valeur("remediation")||"Prévoir une reprise ciblée selon les difficultés constatées lors de l'évaluation.")}</p>`;
 }
 html+=`<p class="small">Document généré automatiquement. Vérifier et adapter les contenus, les consignes, les résultats attendus et la durée à la notion enseignée, au niveau des apprenants et aux documents officiels applicables.</p>`;
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
 if(confirm("Effacer tous les champs du formulaire ?")){
  $("form").reset();
 }
});
</script>
</body>
</html>
