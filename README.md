
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Bot pédagogique APC Bénin</title>
<style>
:root{--vert:#176534;--clair:#eaf5ed;--bord:#cbd8ce}
*{box-sizing:border-box}
body{margin:0;font-family:Arial,sans-serif;background:#f0f5f1;color:#203328;line-height:1.5}
header{background:var(--vert);color:white;text-align:center;padding:22px 12px}
header h1{margin:0;font-size:24px}
main{width:min(1000px,94%);margin:20px auto}
.panel,#fiche{background:white;border:1px solid var(--bord);border-radius:10px;padding:18px;margin-bottom:20px}
h2,h3{color:var(--vert)}
h2{margin-top:0}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:14px}
label{display:block;font-weight:bold;margin-bottom:5px}
input,select,textarea{width:100%;padding:11px;border:1px solid #aabbb0;border-radius:6px;font:inherit;background:white}
textarea{min-height:75px;resize:vertical}
button{border:0;border-radius:6px;padding:12px 16px;margin:8px 6px 0 0;background:var(--vert);color:white;font-size:16px;font-weight:bold;cursor:pointer}
.secondary{background:#56665c!important}
.print{background:#145b9a!important}
#fiche{display:none}
.entete{text-align:center;border-bottom:2px solid var(--vert);padding-bottom:12px}
.info{display:grid;grid-template-columns:repeat(auto-fit,minmax(190px,1fr));gap:8px;margin:15px 0}
.info div{background:var(--clair);padding:9px;border-radius:5px;overflow-wrap:anywhere}
.phase{border:1px solid var(--bord);border-radius:6px;padding:12px;margin:12px 0;break-inside:avoid}
.phase h3{margin-top:0}
table{width:100%;border-collapse:collapse;margin:12px 0}
th,td{border:1px solid #9ba99f;padding:8px;text-align:left;vertical-align:top}
th{background:var(--clair)}
.note{font-size:13px;color:#526258}
@media print{
 body{background:white;color:black;font-size:11pt}
 header,#formulaire,.actions,.note{display:none!important}
 main{width:100%;margin:0}
 #fiche{display:block!important;border:0;padding:0;margin:0}
 .phase,.info div{break-inside:avoid}
}
</style>
</head>
<body>
<header>
<h1>Bot pédagogique APC Bénin</h1>
<p>Préparation des fiches pédagogiques du primaire</p>
</header>

<main>
<section class="panel" id="formulaire">
<h2>Préparer une leçon</h2>
<p>Choisis la classe et la discipline, puis sélectionne une notion ou saisis ton propre titre.</p>

<div class="grid">
<div>
<label for="classe">Classe</label>
<select id="classe">
<option>CI</option><option>CP</option><option selected>CE1</option>
<option>CE2</option><option>CM1</option><option>CM2</option>
</select>
</div>

<div>
<label for="discipline">Discipline</label>
<select id="discipline">
<option>Français</option>
<option>Mathématiques - Arithmétique</option>
<option>Mathématiques - Géométrie</option>
<option>Mathématiques - Mesures</option>
<option>ES - Morale</option>
<option>ES - Civisme</option>
<option>ES - Histoire</option>
<option>ES - Géographie</option>
<option>ES - Langues et culture</option>
<option>EST</option>
<option>EA - Dessin</option>
<option>EA - Chant</option>
<option>EA - Travaux manuels</option>
<option>EA - Poésie</option>
<option>EA - Conte</option>
<option>EA - Couture</option>
<option>EPS</option>
</select>
</div>

<div>
<label for="notionCatalogue">Notions proposées</label>
<select id="notionCatalogue">
<option value="">-- Choisir une notion --</option>
</select>
</div>

<div>
<label for="notion">Notion ou titre de la leçon</label>
<input id="notion" placeholder="Ex. : Les diphtongues" required>
</div>

<div>
<label for="duree">Durée en minutes</label>
<input id="duree" type="number" min="5" value="30">
</div>

<div>
<label for="semaine">Semaine / période</label>
<input id="semaine" placeholder="Ex. : Semaine 1">
</div>

<div>
<label for="ecole">École</label>
<input id="ecole" placeholder="Nom de l'école">
</div>

<div>
<label for="enseignant">Enseignant</label>
<input id="enseignant" placeholder="Nom et prénom">
</div>

<div>
<label for="effectif">Effectif</label>
<input id="effectif" type="number" min="1" placeholder="Ex. : 35">
</div>

<div>
<label for="objectif">Objectif d'apprentissage</label>
<textarea id="objectif" placeholder="À la fin, l'apprenant sera capable de..."></textarea>
</div>

<div>
<label for="competence">Compétence visée</label>
<textarea id="competence" placeholder="Compétence travaillée"></textarea>
</div>

<div>
<label for="resultats">Résultats attendus</label>
<textarea id="resultats" placeholder="Ce que les apprenants doivent réussir"></textarea>
</div>

<div>
<label for="prerequis">Prérequis</label>
<textarea id="prerequis" placeholder="Connaissances déjà acquises"></textarea>
</div>

<div>
<label for="materiel">Matériel et supports</label>
<textarea id="materiel" placeholder="Tableau, images, ardoises, objets..."></textarea>
</div>

<div>
<label for="consigne">Consigne principale</label>
<textarea id="consigne" placeholder="Travail demandé aux apprenants"></textarea>
</div>

<div>
<label for="evaluation">Évaluation / exercice</label>
<textarea id="evaluation" placeholder="Questions ou tâches d'évaluation"></textarea>
</div>
</div>

<div class="actions">
<button type="button" onclick="generer()">Générer le document</button>
<button type="button" class="secondary" onclick="reinitialiser()">Effacer les champs</button>
</div>
<p class="note">Le catalogue est une base de travail provisoire. Vérifie les notions et leur progression dans les programmes et guides pédagogiques officiels du Bénin.</p>
</section>

<section id="fiche">
<div class="entete">
<h2>FICHE DE PRÉPARATION PÉDAGOGIQUE</h2>
<p>Approche par compétences (APC) — Bénin</p>
</div>
<div id="contenuFiche"></div>
<div class="actions">
<button type="button" class="print" onclick="window.print()">Imprimer / Enregistrer en PDF</button>
<button type="button" class="secondary" onclick="modifierFiche()">Modifier la fiche</button>
</div>
</section>
</main>

<script>
const catalogue = {
"CI":{
"Français":["Langage oral","Écoute et compréhension","Vocabulaire de la classe","Reconnaissance des sons","Préparation à l'écriture"],
"Mathématiques - Arithmétique":["Dénombrement","Reconnaissance des nombres","Comparaison de quantités","Petites situations d'addition"],
"Mathématiques - Géométrie":["Repérage dans l'espace","Formes simples","Lignes et tracés"],
"Mathématiques - Mesures":["Comparer des longueurs","Comparer des grandeurs","Repérage dans le temps"],
"ES - Morale":["Politesse","Respect des autres","Partage et entraide"],
"ES - Civisme":["Règles de la classe","Respect du matériel collectif"],
"ES - Histoire":["La famille et les souvenirs"],
"ES - Géographie":["La maison et l'école"],
"ES - Langues et culture":["Salutations","Comptines et traditions locales"],
"EST":["Le corps humain","Les animaux","Les plantes","Hygiène corporelle"],
"EA - Dessin":["Traits et formes","Dessin libre"],
"EA - Chant":["Comptines","Chants simples"],
"EA - Travaux manuels":["Pliage simple","Modelage"],
"EA - Poésie":["Récitation de comptines"],
"EA - Conte":["Écouter et raconter une histoire"],
"EA - Couture":["Découverte des matériaux et des gestes simples"],
"EPS":["Marcher et courir","Sauter","Jeux moteurs"]
},
"CP":{
"Français":["Alphabet et lettres","Sons et syllabes","Lecture de mots simples","Lecture de phrases","Copie et écriture","Vocabulaire courant"],
"Mathématiques - Arithmétique":["Nombres et quantités","Comparaison des nombres","Addition","Soustraction","Résolution de petits problèmes"],
"Mathématiques - Géométrie":["Lignes droites et courbes","Figures usuelles","Repérage spatial"],
"Mathématiques - Mesures":["Longueurs","Temps","Monnaie","Comparaison de masses"],
"ES - Morale":["Respect","Honnêteté","Entraide"],
"ES - Civisme":["Règles de vie collective","Respect des biens publics"],
"ES - Histoire":["La famille","Événements de la vie"],
"ES - Géographie":["L'école et le quartier","Se repérer dans son environnement"],
"ES - Langues et culture":["Salutations","Proverbes et chants locaux"],
"EST":["Les êtres vivants","Les plantes","L'eau","Hygiène et santé"],
"EA - Dessin":["Lignes et formes","Dessiner des objets"],
"EA - Chant":["Chants enfantins","Rythmes simples"],
"EA - Travaux manuels":["Découpage","Collage","Pliage"],
"EA - Poésie":["Mémorisation de poèmes courts"],
"EA - Conte":["Compréhension d'un conte"],
"EA - Couture":["Découverte des tissus et fils"],
"EPS":["Courses simples","Sauts","Lancers","Jeux collectifs simples"]
},
"CE1":{
"Français":["Les diphtongues","Lecture et compréhension","Le vocabulaire","La phrase déclarative et interrogative","Le nom et le déterminant","Le sujet et le verbe","Le présent de l'indicatif","L'orthographe","L'expression orale","L'expression écrite"],
"Mathématiques - Arithmétique":["Les nombres","Comparaison des nombres","L'addition","La soustraction","La multiplication","Les problèmes numériques"],
"Mathématiques - Géométrie":["Les lignes","Les figures géométriques","Les solides","Le repérage dans l'espace"],
"Mathématiques - Mesures":["Les longueurs","La monnaie","Le temps","Les mesures de capacité"],
"ES - Morale":["Respect et tolérance","Solidarité","Honnêteté"],
"ES - Civisme":["Droits et devoirs de l'enfant","Règles de vie collective","Protection des biens publics"],
"ES - Histoire":["La famille et son histoire","Les événements du passé"],
"ES - Géographie":["Le village ou le quartier","L'environnement proche","Les activités locales"],
"ES - Langues et culture":["Contes et proverbes","Langues locales","Traditions du milieu"],
"EST":["Les êtres vivants","Les plantes et leurs besoins","L'eau et ses usages","Hygiène et santé","Objets techniques du quotidien"],
"EA - Dessin":["Dessin d'observation","Formes et motifs"],
"EA - Chant":["Chants et rythmes","Chant collectif"],
"EA - Travaux manuels":["Découpage et assemblage","Fabrication d'objets simples"],
"EA - Poésie":["Lecture expressive","Mémorisation d'un poème"],
"EA - Conte":["Comprendre et raconter un conte"],
"EA - Couture":["Matériaux et gestes de base"],
"EPS":["Courses et relais","Sauts","Lancers","Jeux collectifs"]
},
"CE2":{
"Français":["Lecture et compréhension","Vocabulaire et familles de mots","Types de phrases","Le nom, l'adjectif et le déterminant","Conjugaison au présent","Passé et futur","Accords simples","Production écrite"],
"Mathématiques - Arithmétique":["Numération","Addition et soustraction","Multiplication","Division en situations simples","Résolution de problèmes"],
"Mathématiques - Géométrie":["Droites et segments","Angles et figures","Polygones","Solides"],
"Mathématiques - Mesures":["Longueurs et conversions","Masses","Capacités","Durées","Monnaie"],
"ES - Morale":["Justice et respect","Responsabilité","Coopération"],
"ES - Civisme":["Symboles et règles civiques","Droits et devoirs","Protection du bien commun"],
"ES - Histoire":["Repères du passé","Histoire du milieu"],
"ES - Géographie":["Paysages locaux","Activités humaines","Protection de l'environnement"],
"ES - Langues et culture":["Traditions","Proverbes","Récits du milieu"],
"EST":["Corps humain et santé","Animaux et plantes","Eau et environnement","Matières et objets techniques"],
"EA - Dessin":["Dessin d'observation","Décoration et motifs"],
"EA - Chant":["Chants collectifs","Rythme et mélodie"],
"EA - Travaux manuels":["Assemblage","Fabrication et recyclage"],
"EA - Poésie":["Compréhension et récitation","Expression poétique"],
"EA - Conte":["Structure du conte","Récit oral"],
"EA - Couture":["Assemblage simple de matériaux"],
"EPS":["Course de vitesse","Endurance adaptée","Sauts et lancers","Jeux collectifs"]
},
"CM1":{
"Français":["Lecture approfondie","Vocabulaire et sens des mots","Nature et fonction des mots","Types et formes de phrases","Conjugaison","Accords dans le groupe nominal","Orthographe grammaticale","Production de textes"],
"Mathématiques - Arithmétique":["Numération et grands nombres","Opérations sur les nombres","Multiples et diviseurs selon le programme","Fractions en situations","Problèmes à plusieurs étapes"],
"Mathématiques - Géométrie":["Droites perpendiculaires et parallèles","Angles","Polygones","Symétrie","Solides"],
"Mathématiques - Mesures":["Mesures de longueur","Mesures de masse","Capacités","Durées","Périmètres et aires selon le programme"],
"ES - Morale":["Solidarité et justice","Responsabilité personnelle","Résolution pacifique des conflits"],
"ES - Civisme":["Institutions et règles civiques","Symboles nationaux","Droits et devoirs","Protection des biens publics"],
"ES - Histoire":["Repères historiques","Histoire du Bénin selon le programme"],
"ES - Géographie":["Milieux naturels","Régions et activités du Bénin selon le programme","Environnement"],
"ES - Langues et culture":["Patrimoine culturel","Traditions et langues du milieu"],
"EST":["Santé et hygiène","Écosystèmes et êtres vivants","Matière et énergie","Objets techniques","Environnement"],
"EA - Dessin":["Dessin d'observation","Composition et décoration"],
"EA - Chant":["Chant collectif","Rythme et expression musicale"],
"EA - Travaux manuels":["Conception et fabrication d'objets","Réutilisation de matériaux"],
"EA - Poésie":["Lecture expressive","Étude et récitation de poèmes"],
"EA - Conte":["Structure narrative","Expression orale"],
"EA - Couture":["Techniques élémentaires d'assemblage"],
"EPS":["Course et relais","Endurance adaptée","Sauts","Lancers","Jeux collectifs"]
},
"CM2":{
"Français":["Compréhension de textes","Vocabulaire et expression","Grammaire","Analyse de la phrase","Conjugaison","Accords et orthographe","Rédaction et résumé","Expression orale"],
"Mathématiques - Arithmétique":["Numération","Opérations","Fractions et nombres décimaux selon le programme","Proportionnalité selon le programme","Résolution de problèmes"],
"Mathématiques - Géométrie":["Droites et angles","Triangles et quadrilatères","Symétrie","Solides","Construction géométrique"],
"Mathématiques - Mesures":["Conversions de mesures","Périmètres","Aires","Volumes selon le programme","Durées et monnaie"],
"ES - Morale":["Responsabilité et solidarité","Paix et tolérance","Prévention des conflits"],
"ES - Civisme":["Citoyenneté","Institutions du Bénin selon le programme","Droits et devoirs","Protection du bien commun"],
"ES - Histoire":["Grandes périodes et repères historiques du programme","Histoire du Bénin"],
"ES - Géographie":["Géographie du Bénin","Population et activités","Environnement et ressources"],
"ES - Langues et culture":["Patrimoine culturel béninois","Langues et traditions","Valeurs culturelles"],
"EST":["Santé et prévention","Environnement et écosystèmes","Matière et énergie","Technologie et objets techniques"],
"EA - Dessin":["Dessin d'observation","Composition artistique"],
"EA - Chant":["Chant collectif","Expression musicale"],
"EA - Travaux manuels":["Conception et réalisation d'objets","Réemploi des matériaux"],
"EA - Poésie":["Étude et récitation de poèmes","Expression personnelle"],
"EA - Conte":["Récit oral et écrit","Analyse d'un conte"],
"EA - Couture":["Techniques d'assemblage adaptées au programme"],
"EPS":["Course et relais","Endurance adaptée","Sauts et lancers","Jeux collectifs et coopération"]
}
};

function valeur(id){
 return document.getElementById(id).value.trim();
}

function echapper(texte){
 return String(texte).replace(/[&<>"']/g,function(c){
  return {"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c];
 });
}

function afficher(texte,defaut){
 return echapper(texte||defaut||"À compléter.");
}

function chargerNotions(){
 const classe=valeur("classe");
 const discipline=valeur("discipline");
 const select=document.getElementById("notionCatalogue");
 select.innerHTML='<option value="">-- Choisir une notion --</option>';
 const notions=(catalogue[classe]&&catalogue[classe][discipline])||[];
 notions.forEach(function(notion){
  const option=document.createElement("option");
  option.value=notion;
  option.textContent=notion;
  select.appendChild(option);
 });
}

function choisirNotion(){
 const select=document.getElementById("notionCatalogue");
 if(select.value) document.getElementById("notion").value=select.value;
}

function generer(){
 const notion=valeur("notion");
 if(!notion){
  alert("Veuillez choisir ou saisir une notion.");
  document.getElementById("notion").focus();
  return;
 }

 const duree=Math.max(5,Number(valeur("duree"))||30);
 const phases=[
  {titre:"1. Mise en situation et motivation",pct:10,
   ens:"Présente une situation concrète, fait observer les supports et annonce le problème à résoudre.",
   app:"Observe, écoute, décrit la situation et exprime ses premières idées."},
  {titre:"2. Recherche et exploration",pct:20,
   ens:"Présente les supports, explique la consigne, organise la recherche et accompagne les apprenants.",
   app:"Cherche individuellement ou en groupe, manipule, observe et propose des réponses."},
  {titre:"3. Mise en commun",pct:20,
   ens:"Fait présenter les résultats, organise les échanges et demande de justifier les réponses.",
   app:"Présente sa démarche, écoute les autres et compare les propositions."},
  {titre:"4. Structuration et synthèse",pct:20,
   ens:"Guide la correction et aide la classe à formuler la règle ou la conclusion essentielle.",
   app:"Formule la conclusion et consigne la synthèse dans son cahier."},
  {titre:"5. Application et entraînement",pct:20,
   ens:"Propose des exercices progressifs et apporte une aide adaptée.",
   app:"Réalise les exercices et explique sa démarche."},
  {titre:"6. Évaluation et remédiation",pct:10,
   ens:"Vérifie les acquis, relève les difficultés et prévoit une remédiation.",
   app:"Répond individuellement et corrige ses erreurs avec accompagnement."}
 ];

 let tempsRestant=duree;
 const phasesHTML=phases.map(function(p,i){
  const minutes=i===phases.length-1?tempsRestant:Math.round(duree*p.pct/100);
  if(i!==phases.length-1) tempsRestant-=minutes;
  return `<div class="phase">
   <h3>${p.titre} — ${minutes} min</h3>
   <p><strong>Activités de l'enseignant :</strong> ${p.ens}</p>
   <p><strong>Activités des apprenants :</strong> ${p.app}</p>
   <p><strong>Consigne :</strong> ${afficher(valeur("consigne"),"À préciser selon la tâche proposée.")}</p>
   <p><strong>Trace ou résultat attendu :</strong> ${afficher(valeur("resultats"),"À préciser en fonction de l'objectif.")}</p>
  </div>`;
 }).join("");

 const html=`
 <div class="info">
 <div><strong>École :</strong> ${afficher(valeur("ecole"))}</div>
 <div><strong>Classe :</strong> ${afficher(valeur("classe"))}</div>
 <div><strong>Discipline :</strong> ${afficher(valeur("discipline"))}</div>
 <div><strong>Notion :</strong> ${afficher(notion)}</div>
 <div><strong>Durée :</strong> ${duree} minutes</div>
 <div><strong>Semaine / période :</strong> ${afficher(valeur("semaine"))}</div>
 <div><strong>Enseignant :</strong> ${afficher(valeur("enseignant"))}</div>
 <div><strong>Effectif :</strong> ${afficher(valeur("effectif"))}</div>
 </div>

 <h3>I. Compétence visée</h3>
 <p>${afficher(valeur("competence"),"À compléter à partir du programme officiel.")}</p>

 <h3>II. Objectif d'apprentissage</h3>
 <p>${afficher(valeur("objectif"),"À préciser en fonction de la notion étudiée.")}</p>

 <h3>III. Résultats attendus</h3>
 <p>${afficher(valeur("resultats"),"À définir selon l'objectif d'apprentissage.")}</p>

 <h3>IV. Prérequis</h3>
 <p>${afficher(valeur("prerequis"))}</p>

 <h3>V. Matériel et supports</h3>
 <p>${afficher(valeur("materiel"))}</p>

 <h3>VI. Déroulement de la séance</h3>
 <table><thead><tr><th>Phase</th><th>Activités de l'enseignant</th><th>Activités des apprenants</th></tr></thead>
 <tbody>${phases.map(function(p){
 return `<tr><td>${p.titre}</td><td>${p.ens}</td><td>${p.app}</td></tr>`;
 }).join("")}</tbody></table>
 ${phasesHTML}

 <h3>VII. Évaluation</h3>
 <p>${afficher(valeur("evaluation"),"Prévoir une tâche individuelle en rapport direct avec l'objectif.")}</p>

 <h3>VIII. Remédiation et prolongement</h3>
 <p>Prévoir une activité adaptée aux difficultés constatées et un exercice de réinvestissement pour les apprenants ayant réussi.</p>

 <h3>IX. Bilan de l'enseignant</h3>
 <p>Objectif atteint : ☐ Oui ☐ Partiellement ☐ Non</p>
 <p>Difficultés observées : ...............................................................................</p>
 <p>Décisions pour la prochaine séance : ............................................................</p>

 <p><em>Important : catalogue de notions provisoire. Vérifier les contenus, compétences, progressions et phases dans les documents pédagogiques officiels du Bénin.</em></p>
 `;

 document.getElementById("contenuFiche").innerHTML=html;
 document.getElementById("fiche").style.display="block";
 document.getElementById("fiche").scrollIntoView({behavior:"smooth"});
}

function modifierFiche(){
 document.getElementById("formulaire").scrollIntoView({behavior:"smooth"});
}

function reinitialiser(){
 if(!confirm("Effacer tous les champs ?")) return;
 document.querySelectorAll("#formulaire input,#formulaire textarea").forEach(function(el){el.value="";});
 document.getElementById("classe").value="CE1";
 document.getElementById("discipline").value="Français";
 document.getElementById("duree").value="30";
 document.getElementById("notionCatalogue").value="";
 document.getElementById("fiche").style.display="none";
 document.getElementById("contenuFiche").innerHTML="";
 chargerNotions();
}

document.addEventListener("DOMContentLoaded",function(){
 document.getElementById("classe").addEventListener("change",chargerNotions);
 document.getElementById("discipline").addEventListener("change",chargerNotions);
 document.getElementById("notionCatalogue").addEventListener("change",choisirNotion);
 chargerNotions();
});
</script>
</body>
</html>
