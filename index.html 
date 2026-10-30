<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#185d39">
<title>Bot pédagogique APC Bénin</title>
<style>
:root{--vert:#185d39;--clair:#edf5ef;--or:#d5a53b}
*{box-sizing:border-box}
body{margin:0;background:#f2f5f2;color:#202820;font-family:Arial,sans-serif;line-height:1.5}
header{background:var(--vert);color:white;padding:24px 15px;text-align:center}
header h1{margin:0;font-size:26px}
header p{margin:7px 0 0}
main{max-width:1050px;margin:22px auto;padding:0 12px}
.panel{background:white;border-radius:12px;padding:20px;margin-bottom:18px;box-shadow:0 2px 9px #0001}
h2{color:var(--vert);margin-top:0}
.formgrid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:14px}
label{display:block;font-weight:bold;margin-bottom:5px}
input,select,textarea{width:100%;padding:10px;border:1px solid #bac7bc;border-radius:6px;font:inherit;background:white}
textarea{min-height:85px;resize:vertical}
.full{grid-column:1/-1}
.buttons{display:flex;flex-wrap:wrap;gap:9px;margin-top:16px}
button{border:0;border-radius:7px;padding:11px 16px;background:var(--vert);color:white;font-weight:bold;cursor:pointer}
button.secondary{background:#526257}
button.gold{background:#9a6c08}
button:hover{filter:brightness(.94)}
#message{margin-top:10px;font-weight:bold;color:var(--vert)}
#fiche{background:white;padding:22px;border:1px solid #d5ddd6;border-radius:8px;overflow-wrap:anywhere}
#fiche h2,#fiche h3{text-align:center;color:var(--vert)}
#fiche h3{border-bottom:1px solid #b6c8ba;padding-bottom:5px}
.fiche-entete{text-align:center;border:2px solid var(--vert);padding:12px;margin-bottom:15px}
table{border-collapse:collapse;width:100%;margin:12px 0}
th,td{border:1px solid #89988d;padding:8px;text-align:left;vertical-align:top}
th{background:var(--clair)}
.phase-editor{border:1px solid #d5ddd6;border-radius:8px;padding:14px;margin:12px 0;background:#fbfdfb}
.phase-editor h3{margin:0 0 10px;color:var(--vert);font-size:17px}
.note{font-size:13px;color:#59645b}
footer{text-align:center;padding:20px;color:#59645b}
@media(max-width:600px){.panel{padding:14px}header h1{font-size:22px}#fiche{padding:12px}table{font-size:13px}th,td{padding:5px}}
@media print{
 body{background:white}
 header,.formulaire,.actions,footer{display:none!important}
 main{max-width:none;margin:0;padding:0}
 .panel{box-shadow:none;border:0;padding:0;margin:0}
 #fiche{border:0;padding:0}
 @page{size:A4;margin:15mm}
}
</style>
</head>
<body>
<header>
  <h1>Bot pédagogique APC Bénin</h1>
  <p>Préparation des fiches pédagogiques du primaire</p>
</header>

<main>
<section class="panel formulaire">
  <h2>Préparer une leçon</h2>
  <p>Remplis les champs puis clique sur « Générer la fiche ». Le catalogue est une base de travail à compléter et à vérifier avec les programmes et guides officiels.</p>

  <div class="formgrid">
    <div><label for="classe">Classe</label><select id="classe">
      <option>CI</option><option>CP</option><option selected>CE1</option><option>CE2</option><option>CM1</option><option>CM2</option>
    </select></div>
    <div><label for="discipline">Discipline</label><select id="discipline">
      <option>Français</option>
      <option>Mathématiques — Arithmétique</option>
      <option>Mathématiques — Géométrie</option>
      <option>Mathématiques — Mesures</option>
      <option>Éducation sociale — Morale</option>
      <option>Éducation sociale — Civisme</option>
      <option>Éducation sociale — Histoire-Géographie</option>
      <option>Éducation sociale — Langues et culture</option>
      <option>EST</option>
      <option>Éducation artistique — Dessin</option>
      <option>Éducation artistique — Chant</option>
      <option>Éducation artistique — Travaux manuels</option>
      <option>Éducation artistique — Poésie</option>
      <option>Éducation artistique — Conte</option>
      <option>Éducation artistique — Couture</option>
      <option>EPS</option>
    </select></div>
    <div><label for="notionCatalogue">Notion du catalogue</label><select id="notionCatalogue"></select></div>
    <div><label for="titre">Titre de la leçon</label><input id="titre" placeholder="Titre de la leçon"></div>
    <div><label for="ecole">École</label><input id="ecole" placeholder="Nom de l'école"></div>
    <div><label for="enseignant">Enseignant(e)</label><input id="enseignant" placeholder="Nom de l'enseignant(e)"></div>
    <div><label for="date">Date</label><input id="date" type="date"></div>
    <div><label for="duree">Durée totale (minutes)</label><input id="duree" type="number" min="1" value="30"></div>
    <div><label for="sa">Situation d’apprentissage (SA)</label><input id="sa" placeholder="Ex. : SA 1"></div>
    <div><label for="sequence">Séquence</label><input id="sequence" placeholder="Ex. : Séquence 1"></div>
    <div><label for="numero">Numéro de fiche</label><input id="numero" placeholder="Ex. : Fiche n° 1"></div>
    <div><label for="periode">Période / trimestre</label><input id="periode" placeholder="Période ou trimestre"></div>

    <div class="full"><label for="competence">Compétence disciplinaire visée</label><textarea id="competence" placeholder="À renseigner selon le programme officiel"></textarea></div>
    <div class="full"><label for="competencesTrans">Compétences transversales et transdisciplinaires</label><textarea id="competencesTrans"></textarea></div>
    <div class="full"><label for="connaissances">Connaissances et techniques</label><textarea id="connaissances"></textarea></div>
    <div class="full"><label for="objectif">Objectif d’apprentissage / résultat final attendu</label><textarea id="objectif"></textarea></div>
    <div class="full"><label for="prerequis">Prérequis</label><textarea id="prerequis"></textarea></div>
    <div class="full"><label for="situation">Situation de départ / situation-problème</label><textarea id="situation"></textarea></div>
    <div class="full"><label for="strategies">Stratégies d’enseignement et d’apprentissage</label><textarea id="strategies" placeholder="Travail individuel, en groupe, collectif, par paire…"></textarea></div>
    <div class="full"><label for="materiel">Matériel didactique</label><textarea id="materiel"></textarea></div>
    <div class="full"><label for="trace">Trace écrite / synthèse à retenir</label><textarea id="trace"></textarea></div>
    <div class="full"><label for="remediation">Remédiation prévue</label><textarea id="remediation"></textarea></div>
    <div class="full"><label for="projection">Projection / réinvestissement</label><textarea id="projection"></textarea></div>
  </div>

  <h2 style="margin-top:24px">Déroulement détaillé</h2>
  <p class="note">Les durées des phases sont indicatives. Adapte-les à la durée totale de la séance. Tu peux modifier les consignes, stratégies, résultats attendus et durées.</p>
  <div id="phases"></div>
  <div class="buttons actions">
    <button type="button" id="generer">Générer la fiche</button>
    <button type="button" class="secondary" id="copier">Copier le texte</button>
    <button type="button" class="gold" id="imprimer">Imprimer / PDF</button>
    <button type="button" class="secondary" id="vider">Vider le formulaire</button>
  </div>
  <div id="message" role="status" aria-live="polite"></div>
</section>

<section class="panel">
  <h2>FICHE PÉDAGOGIQUE APC BÉNIN</h2>
  <div id="fiche">Remplis le formulaire puis clique sur « Générer la fiche ».</div>
</section>
</main>

<footer>Bot pédagogique APC Bénin — outil d’aide à la préparation pédagogique.</footer>

<script>
"use strict";

const catalogue = {
  "CI": {
    "Français":["Écoute et compréhension de consignes","Expression orale en situation","Découverte de sons et de mots"],
    "Mathématiques — Arithmétique":["Dénombrement d’objets","Comparaison de collections","Premières situations d’addition"],
    "Mathématiques — Géométrie":["Repérage dans l’espace","Reconnaissance de formes simples"],
    "Mathématiques — Mesures":["Comparaison de grandeurs","Repérage du temps"],
    "Éducation sociale — Morale":["Politesse et respect","Partage et entraide"],
    "Éducation sociale — Civisme":["Règles de vie en classe","Respect du matériel"],
    "Éducation sociale — Histoire-Géographie":["La famille et l’école","Le milieu de vie proche"],
    "Éducation sociale — Langues et culture":["Expressions du milieu de vie"],
    "EST":["Hygiène corporelle","Propreté du cadre de vie"],
    "Éducation artistique — Dessin":["Tracés et dessin libre"],
    "Éducation artistique — Chant":["Chants et comptines"],
    "Éducation artistique — Travaux manuels":["Manipulation et assemblage"],
    "Éducation artistique — Poésie":["Mémorisation de comptines"],
    "Éducation artistique — Conte":["Écoute d’un conte"],
    "Éducation artistique — Couture":["Découverte de matériaux"],
    "EPS":["Marcher et courir","Sauter et se déplacer"]
  },
  "CP": {
    "Français":["Lecture et compréhension de consignes","Lecture et écriture de syllabes et de mots","Copie de mots et de phrases","Vocabulaire du milieu de vie"],
    "Mathématiques — Arithmétique":["Les nombres de 0 à 99 : comptage et décomptage","Les nombres de 0 à 99 : lecture et écriture en chiffres et en lettres","Les nombres de 0 à 99 : comparaison et rangement","Addition et soustraction des nombres de 0 à 99","Résolution de problèmes sur les nombres de 0 à 99","Le nombre 100 : composition et représentation","Le nombre 100 : identification, lecture et écriture","Intégration des acquis : numération, addition et soustraction","Intégration des acquis : résolution de problèmes"],
    "Mathématiques — Géométrie":["Les solides géométriques : identification et description du cube","Le cube : faces, sommets et arêtes","Résolution de problèmes portant sur les solides géométriques"],
    "Mathématiques — Mesures":["Comparaison de longueurs","Mesures à partir d’objets du milieu de vie"],
    "Éducation sociale — Morale":["Respect et entraide","Politesse et règles de vie"],
    "Éducation sociale — Civisme":["Respect du matériel collectif","Règles de vie à l’école"],
    "Éducation sociale — Histoire-Géographie":["La famille et l’école","Le milieu de vie proche"],
    "Éducation sociale — Langues et culture":["Expressions et pratiques culturelles du milieu"],
    "EST":["Hygiène et santé","Alimentation et protection des aliments","Les différents types de marmites","Utilisation prudente du foyer et du réchaud"],
    "Éducation artistique — Dessin":["Dessin d’objets familiers"],
    "Éducation artistique — Chant":["Chants et comptines"],
    "Éducation artistique — Travaux manuels":["Découpage, pliage et assemblage"],
    "Éducation artistique — Poésie":["Récitation d’un poème court"],
    "Éducation artistique — Conte":["Écoute et restitution d’un conte"],
    "Éducation artistique — Couture":["Découverte des gestes et matériaux de base"],
    "EPS":["Actions locomotrices et non locomotrices","Saut vers l’avant","Saut vers l’arrière","Saut vers l’avant, saut vers l’arrière","Saut vers le haut","Saut vers le bas","Saut sur le côté","Préparation, réalisation et amélioration d’une action motrice","Retour au calme et rangement du matériel"]
  },
  "CE1": {
    "Français":["Les diphtongues","Lecture et compréhension de textes courts","Grammaire : la phrase","Vocabulaire du quotidien","Production de phrases simples"],
    "Mathématiques — Arithmétique":["Numération et opérations","Addition et soustraction","Multiplication : premières situations","Résolution de problèmes"],
    "Mathématiques — Géométrie":["Figures géométriques planes","Solides usuels"],
    "Mathématiques — Mesures":["Longueurs et unités usuelles","Mesure du temps"],
    "Éducation sociale — Morale":["Respect et solidarité"],
    "Éducation sociale — Civisme":["Droits et devoirs à l’école"],
    "Éducation sociale — Histoire-Géographie":["Famille, école et communauté"],
    "Éducation sociale — Langues et culture":["Langues et pratiques culturelles locales"],
    "EST":["Hygiène et santé","Environnement et sécurité"],
    "Éducation artistique — Dessin":["Dessin d’observation"],
    "Éducation artistique — Chant":["Chants et rythmes"],
    "Éducation artistique — Travaux manuels":["Pliage et fabrication d’objets"],
    "Éducation artistique — Poésie":["Récitation et diction"],
    "Éducation artistique — Conte":["Compréhension et restitution d’un conte"],
    "Éducation artistique — Couture":["Gestes simples et matériaux"],
    "EPS":["Actions motrices et jeux collectifs"]
  },
  "CE2": {
    "Français":["Lecture et compréhension","Grammaire et conjugaison","Orthographe et vocabulaire","Production écrite"],
    "Mathématiques — Arithmétique":["Numération","Opérations sur les nombres","Résolution de problèmes"],
    "Mathématiques — Géométrie":["Droites et figures planes","Solides géométriques"],
    "Mathématiques — Mesures":["Longueurs, masses et capacités","Durées et monnaie"],
    "Éducation sociale — Morale":["Responsabilité et solidarité"],
    "Éducation sociale — Civisme":["Règles collectives et biens publics"],
    "Éducation sociale — Histoire-Géographie":["Milieu local et vie communautaire"],
    "Éducation sociale — Langues et culture":["Patrimoine culturel local"],
    "EST":["Santé, hygiène et environnement"],
    "Éducation artistique — Dessin":["Dessin et composition"],
    "Éducation artistique — Chant":["Chant et rythme"],
    "Éducation artistique — Travaux manuels":["Fabrication et assemblage"],
    "Éducation artistique — Poésie":["Récitation expressive"],
    "Éducation artistique — Conte":["Conte et expression orale"],
    "Éducation artistique — Couture":["Techniques manuelles simples"],
    "EPS":["Course, saut et jeux collectifs"]
  },
  "CM1": {
    "Français":["Lecture et compréhension de textes","Grammaire et conjugaison","Orthographe et vocabulaire","Production de textes"],
    "Mathématiques — Arithmétique":["Numération et opérations","Fractions et nombres décimaux","Résolution de problèmes"],
    "Mathématiques — Géométrie":["Figures et propriétés géométriques","Construction de figures"],
    "Mathématiques — Mesures":["Longueurs, aires et périmètres","Masses, capacités et durées"],
    "Éducation sociale — Morale":["Droits, devoirs et solidarité"],
    "Éducation sociale — Civisme":["Citoyenneté et biens communs"],
    "Éducation sociale — Histoire-Géographie":["Histoire et géographie du milieu"],
    "Éducation sociale — Langues et culture":["Cultures et patrimoine"],
    "EST":["Santé, environnement et techniques usuelles"],
    "Éducation artistique — Dessin":["Dessin d’observation et composition"],
    "Éducation artistique — Chant":["Chant et expression musicale"],
    "Éducation artistique — Travaux manuels":["Réalisation d’objets"],
    "Éducation artistique — Poésie":["Récitation et expression"],
    "Éducation artistique — Conte":["Récit et compréhension"],
    "Éducation artistique — Couture":["Techniques de base"],
    "EPS":["Athlétisme et jeux collectifs"]
  },
  "CM2": {
    "Français":["Lecture et analyse de textes","Grammaire et conjugaison","Orthographe et vocabulaire","Rédaction"],
    "Mathématiques — Arithmétique":["Numération et opérations","Fractions et nombres décimaux","Proportionnalité et problèmes"],
    "Mathématiques — Géométrie":["Figures, angles et constructions","Solides géométriques"],
    "Mathématiques — Mesures":["Périmètres, aires et volumes","Mesures et conversions"],
    "Éducation sociale — Morale":["Responsabilité et solidarité"],
    "Éducation sociale — Civisme":["Citoyenneté et vie démocratique"],
    "Éducation sociale — Histoire-Géographie":["Histoire et géographie du Bénin"],
    "Éducation sociale — Langues et culture":["Patrimoine et diversité culturelle"],
    "EST":["Santé, environnement et techniques"],
    "Éducation artistique — Dessin":["Dessin et composition"],
    "Éducation artistique — Chant":["Chant et pratique musicale"],
    "Éducation artistique — Travaux manuels":["Conception et réalisation"],
    "Éducation artistique — Poésie":["Récitation expressive"],
    "Éducation artistique — Conte":["Conte et expression orale"],
    "Éducation artistique — Couture":["Réalisation manuelle"],
    "EPS":["Athlétisme, jeux et activités physiques"]
  }
};

const phasesBase = [
  {nom:"1. Activités préparatoires",duree:5,strategie:"Collectif",consigne:"Prépare-toi, organise le matériel et participe à la mise en train.",attendu:"L’apprenant est prêt et respecte les consignes de sécurité."},
  {nom:"2. Introduction",duree:5,strategie:"Collectif",consigne:"Rappelle les acquis antérieurs. Observe la situation et exprime ce que tu sais.",attendu:"L’apprenant mobilise ses acquis et comprend l’objectif."},
  {nom:"3. Construction / réalisation",duree:10,strategie:"Travail individuel et collectif",consigne:"Observe, décris, analyse la situation et propose une manière de résoudre la tâche.",attendu:"L’apprenant identifie la tâche et propose une démarche."},
  {nom:"4. Exploration et exécution",duree:5,strategie:"Individuel, par paire ou en groupe",consigne:"Réalise la tâche individuellement ou avec un partenaire. Observe et améliore ta production.",attendu:"L’apprenant exécute la tâche et tient compte des observations."},
  {nom:"5. Retour, objectivation et évaluation",duree:3,strategie:"Individuel et collectif",consigne:"Explique ce que tu as appris, ce qui a été difficile et comment tu peux progresser.",attendu:"L’apprenant explique ses apprentissages et montre ce qu’il sait faire."},
  {nom:"6. Post-apprentissage",duree:2,strategie:"Collectif",consigne:"Range le matériel et indique une situation dans laquelle tu pourras réutiliser l’apprentissage.",attendu:"L’apprenant range le matériel et envisage un réinvestissement."}
];

const $ = id => document.getElementById(id);
const champ = id => ($(id)?.value ?? "").trim();
const idsTexte = ["ecole","enseignant","date","duree","sa","sequence","numero","periode","titre","competence","competencesTrans","connaissances","objectif","prerequis","situation","strategies","materiel","trace","remediation","projection"];

function ajouterLigne(label, valeur) {
  const tr = document.createElement("tr");
  const th = document.createElement("th");
  const td = document.createElement("td");
  th.textContent = label;
  td.textContent = valeur || "À compléter";
  tr.append(th, td);
  return tr;
}

function creerChampsPhases() {
  const conteneur = $("phases");
  conteneur.replaceChildren();
  phasesBase.forEach((phase, i) => {
    const bloc = document.createElement("div");
    bloc.className = "phase-editor";
    const titre = document.createElement("h3");
    titre.textContent = phase.nom;
    bloc.appendChild(titre);

    const grille = document.createElement("div");
    grille.className = "formgrid";
    const champs = [
      {id:`duree${i}`,label:"Durée (minutes)",value:phase.duree,type:"number"},
      {id:`strategie${i}`,label:"Stratégie / organisation",value:phase.strategie,type:"text"}
    ];
    champs.forEach(c => {
      const wrap = document.createElement("div");
      const lab = document.createElement("label");
      lab.htmlFor = c.id; lab.textContent = c.label;
      const input = document.createElement("input");
      input.id = c.id; input.type = c.type; input.value = c.value;
      if(c.type === "number") input.min = "0";
      wrap.append(lab,input); grille.appendChild(wrap);
    });
    [
      {id:`consigne${i}`,label:"Consignes / activités de l’enseignant et des apprenants",value:phase.consigne},
      {id:`attendu${i}`,label:"Résultats attendus",value:phase.attendu}
    ].forEach(c => {
      const wrap = document.createElement("div");
      wrap.className = "full";
      const lab = document.createElement("label");
      lab.htmlFor = c.id; lab.textContent = c.label;
      const area = document.createElement("textarea");
      area.id = c.id; area.value = c.value;
      wrap.append(lab,area); grille.appendChild(wrap);
    });
    bloc.appendChild(grille);
    conteneur.appendChild(bloc);
  });
}

function appliquerModele() {
  const classe = champ("classe");
  const discipline = champ("discipline");
  const notion = champ("notionCatalogue");
  if(classe === "CP" && discipline === "EPS" && notion === "Saut vers l’avant, saut vers l’arrière") {
    $("duree").value = 45;
    $("sa").value = "SA 7";
    $("sequence").value = "Séquence 2";
    $("numero").value = "Fiche n° 2";
    $("competence").value = "Agir dans divers contextes de pratique d’activités physiques et interagir dans divers contextes de pratique d’activités physiques (formulation reprise du document fourni).";
    $("connaissances").value = "Réalisation de sauts vers l’avant et vers l’arrière.";
    $("strategies").value = "Travail individuel et par paire ; travail en groupe et collectif ; apprentissage par problème.";
    $("materiel").value = "Terrain adapté, craie ou chaux pour le marquage, fanions, image et autres matériels nécessaires.";
    $("prerequis").value = "Dire comment réaliser un saut vers l’avant et rappeler les règles de sécurité.";
    $("objectif").value = "Réaliser des sauts vers l’avant et vers l’arrière en respectant les consignes et les règles de sécurité.";
    $("situation").value = "Observer une image présentant des sauts, décrire ce qui se passe et proposer comment réaliser les mouvements en sécurité.";
    $("trace").value = "Pour sauter en sécurité, je respecte les consignes, j’observe l’espace disponible et j’écoute les indications de l’enseignant. Les étapes techniques précises doivent être adaptées au guide de la classe.";
    $("remediation").value = "Reprendre la démonstration lentement, aménager la zone de saut et accompagner individuellement les apprenants qui rencontrent des difficultés.";
    $("projection").value = "Réutiliser les techniques apprises pendant les jeux et activités physiques adaptés.";
    const consignes = [
      "Porte ta tenue de sport. Forme les rangs et rejoins le terrain en marchant de façon organisée. Effectue une mise en train adaptée.",
      "Rappelle une activité déjà étudiée. Dis ce que tu sais sur le saut vers l’avant et vers l’arrière. Écoute l’objectif de la séance.",
      "Observe l’image. Décris ce que tu vois. Explique comment réaliser les sauts et indique les mesures de sécurité à prendre.",
      "Propose un ordre d’exécution. Essaie le saut, observe les camarades, compare les manières de faire et réalise les sauts seul puis par paire, selon les possibilités du terrain.",
      "Dis ce que tu as appris, les difficultés rencontrées et comment tu les as surmontées. Montre le mouvement demandé dans des conditions sécurisées.",
      "Effectue le retour au calme adapté au guide. Range le matériel et forme les rangs."
    ];
    const attendus = [
      "L’apprenant est prêt, suit les consignes et participe à la mise en train.",
      "L’apprenant rappelle un acquis et exprime ce qu’il sait du saut.",
      "L’apprenant décrit l’image et identifie les précautions de sécurité.",
      "L’apprenant essaie, observe, compare et améliore sa réalisation.",
      "L’apprenant explique son apprentissage et réalise le mouvement demandé.",
      "L’apprenant revient au calme et range le matériel."
    ];
    const durees = [7,5,8,15,5,5];
    const strategies = ["Collectif","Collectif","Observation et échange collectif","Individuel puis par paire","Individuel et collectif","Collectif"];
    consignes.forEach((v,i) => {
      $(`consigne${i}`).value = v;
      $(`attendu${i}`).value = attendus[i];
      $(`duree${i}`).value = durees[i];
      $(`strategie${i}`).value = strategies[i];
    });
  }
}

function chargerNotions() {
  const classe = champ("classe");
  const discipline = champ("discipline");
  const liste = catalogue[classe]?.[discipline] || ["Notion à préciser selon le programme"];
  const select = $("notionCatalogue");
  select.replaceChildren();
  liste.forEach(notion => {
    const option = document.createElement("option");
    option.value = notion;
    option.textContent = notion;
    select.appendChild(option);
  });
  $("titre").value = liste[0] || "";
  appliquerModele();
}

function lirePhases() {
  return phasesBase.map((p,i) => ({
    nom:p.nom,
    duree:Math.max(0, Number($(`duree${i}`).value) || 0),
    strategie:$(`strategie${i}`).value.trim(),
    consigne:$(`consigne${i}`).value.trim(),
    attendu:$(`attendu${i}`).value.trim()
  }));
}
function repartirDureePhases() {
  const dureeTotale = Math.max(1, Number($("duree").value) || 30);

  const dureesBase = phasesBase.map(p => p.duree);
  const sommeBase = dureesBase.reduce((a, b) => a + b, 0);

  const valeurs = dureesBase.map((d, i) => ({
    index: i,
    valeur: (d / sommeBase) * dureeTotale
  }));

  const durees = valeurs.map(v => Math.floor(v.valeur));

  let reste = dureeTotale -
    durees.reduce((a, b) => a + b, 0);

  valeurs
    .map(v => ({
      index: v.index,
      decimal: v.valeur - Math.floor(v.valeur)
    }))
    .sort((a, b) => b.decimal - a.decimal)
    .forEach(v => {
      if (reste > 0) {
        durees[v.index]++;
        reste--;
      }
    });

  durees.forEach((d, i) => {
    $(`duree${i}`).value = d;
  });
}
function genererFiche() {
  const phases = lirePhases();
  const total = phases.reduce((s,p) => s + p.duree, 0);
  const fiche = $("fiche");
  fiche.replaceChildren();

  const entete = document.createElement("div");
  entete.className = "fiche-entete";
  const h = document.createElement("h2");
  h.textContent = "FICHE DE PRÉPARATION PÉDAGOGIQUE";
  const sous = document.createElement("strong");
  sous.textContent = "Approche par compétences — Bénin";
  entete.append(h,sous);
  fiche.appendChild(entete);

  const meta = document.createElement("table");
  const tbody = document.createElement("tbody");
  [
    ["École",champ("ecole")],["Enseignant(e)",champ("enseignant")],
    ["Classe",champ("classe")],["Discipline",champ("discipline")],
    ["Date",champ("date")],["Durée annoncée",`${champ("duree") || "À compléter"} minutes`],
    ["Situation d’apprentissage",champ("sa")],
    ["Séquence / fiche",`${champ("sequence")} — ${champ("numero")}`],
    ["Période / trimestre",champ("periode")],["Titre",champ("titre")]
  ].forEach(([l,v]) => tbody.appendChild(ajouterLigne(l,v)));
  meta.appendChild(tbody); fiche.appendChild(meta);

  const sections = [
    ["I. CONTENUS DE FORMATION",[
      ["Compétence disciplinaire",champ("competence")],
      ["Compétences transversales et transdisciplinaires",champ("competencesTrans")],
      ["Connaissances et techniques",champ("connaissances")],
      ["Objectif d’apprentissage / résultat final attendu",champ("objectif")],
      ["Prérequis",champ("prerequis")],
      ["Situation de départ / situation-problème",champ("situation")],
      ["Stratégies d’enseignement et d’apprentissage",champ("strategies")],
      ["Matériel didactique",champ("materiel")]
    ]],
    ["III. TRACE ÉCRITE / SYNTHÈSE", [["Synthèse à retenir",champ("trace")]]],
    ["IV. REMÉDIATION", [["Remédiation prévue",champ("remediation")]]],
    ["V. PROJECTION / RÉINVESTISSEMENT", [["Réinvestissement",champ("projection")]]]
  ];

  sections.forEach(([titre, lignes]) => {
    const h3 = document.createElement("h3"); h3.textContent = titre; fiche.appendChild(h3);
    const table = document.createElement("table");
    const body = document.createElement("tbody");
    lignes.forEach(([l,v]) => body.appendChild(ajouterLigne(l,v)));
    table.appendChild(body); fiche.appendChild(table);
  });

  const h3 = document.createElement("h3"); h3.textContent = "II. DÉROULEMENT DÉTAILLÉ"; fiche.appendChild(h3);
  const table = document.createElement("table");
  const thead = document.createElement("thead");
  const trh = document.createElement("tr");
  ["Phases / durée","Consignes et activités","Stratégies","Résultats attendus"].forEach(t => {
    const th = document.createElement("th"); th.textContent = t; trh.appendChild(th);
  });
  thead.appendChild(trh); table.appendChild(thead);
  const tb = document.createElement("tbody");
  phases.forEach(p => {
    const tr = document.createElement("tr");
    [ `${p.nom}\n${p.duree} min`, p.consigne, p.strategie, p.attendu ].forEach(v => {
      const td = document.createElement("td"); td.textContent = v || "À compléter"; tr.appendChild(td);
    });
    tb.appendChild(tr);
  });
  table.appendChild(tb); fiche.appendChild(table);

  const totalP = document.createElement("p");
  totalP.innerHTML = "<strong>Total des durées des phases : </strong>";
  const totalText = document.createTextNode(`${total} minutes. `);
  totalP.appendChild(totalText);
  const avert = document.createElement("strong");
  avert.textContent = total === Number(champ("duree")) ? "Le total correspond à la durée annoncée." : "Attention : vérifie la correspondance avec la durée annoncée.";
  avert.style.color = total === Number(champ("duree")) ? "#185d39" : "#9a6c08";
  totalP.appendChild(avert); fiche.appendChild(totalP);

  const note = document.createElement("p");
  note.className = "note";
  note.textContent = "Document généré par le Bot pédagogique APC Bénin. Les formulations et contenus doivent être vérifiés avec les programmes, guides et documents officiels applicables.";
  fiche.appendChild(note);

  $("message").textContent = "Fiche générée. Vérifie les informations et les durées avant l’impression.";
  return fiche;
}

$("classe").addEventListener("change",chargerNotions);
$("discipline").addEventListener("change",chargerNotions);
$("notionCatalogue").addEventListener("change",() => {
  $("titre").value = champ("notionCatalogue");
  appliquerModele();
});
$("duree").addEventListener("input", repartirDureePhases);
$("generer").addEventListener("click",genererFiche);
$("imprimer").addEventListener("click",() => { genererFiche(); window.print(); });
$("copier").addEventListener("click",async() => {
  genererFiche();
  const texte = $("fiche").innerText;
  try {
    if(navigator.clipboard && window.isSecureContext) {
      await navigator.clipboard.writeText(texte);
      $("message").textContent = "Fiche copiée dans le presse-papiers.";
    } else {
      throw new Error("Presse-papiers non disponible");
    }
  } catch(e) {
    const selection = window.getSelection();
    const range = document.createRange();
    range.selectNodeContents($("fiche"));
    selection.removeAllRanges(); selection.addRange(range);
    $("message").textContent = "Le texte est sélectionné. Fais un appui long puis choisis Copier.";
  }
});
$("vider").addEventListener("click",() => {
  if(!confirm("Effacer les informations du formulaire ?")) return;
  idsTexte.forEach(id => { if($(id)) $(id).value = ""; });
  $("duree").value = 30;
  $("classe").value = "CE1";
  $("discipline").value = "Français";
  creerChampsPhases();
  chargerNotions();
  $("message").textContent = "Formulaire réinitialisé.";
});

creerChampsPhases();
chargerNotions();
</script>
</body>
</html>
