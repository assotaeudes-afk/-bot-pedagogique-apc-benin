HTML

<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Bot pédagogique APC Bénin</title>
<style>
:root {
  --vert: #176534;
  --vert-clair: #eaf5ed;
  --texte: #203329;
  --bordure: #cbd9ce;
}
* { box-sizing: border-box; }
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f1f5f2;
  color: var(--texte);
  line-height: 1.5;
}
header {
  background: linear-gradient(135deg, #104b27, #23834b);
  color: white;
  padding: 24px 16px;
  text-align: center;
}
header h1 { margin: 0 0 5px; font-size: 25px; }
header p { margin: 0; }
main { max-width: 1000px; margin: 22px auto; padding: 0 12px; }
.panel {
  background: white;
  padding: 20px;
  border-radius: 14px;
  margin-bottom: 20px;
  box-shadow: 0 4px 16px #1833230d;
}
h2 {
  color: var(--vert);
  font-size: 20px;
  border-bottom: 2px solid #d9eade;
  padding-bottom: 8px;
  margin-top: 0;
}
h3 { color: var(--vert); margin-bottom: 8px; }
.grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 13px;
}
.field { display: flex; flex-direction: column; gap: 5px; }
.field.full { grid-column: 1 / -1; }
label { font-weight: bold; font-size: 14px; }
input, select, textarea {
  width: 100%;
  padding: 11px;
  border: 1px solid var(--bordure);
  border-radius: 8px;
  font: inherit;
  background: #fff;
}
textarea { min-height: 82px; resize: vertical; }
button {
  border: 0;
  border-radius: 9px;
  padding: 12px 16px;
  font-size: 15px;
  font-weight: bold;
  cursor: pointer;
  margin: 5px 5px 5px 0;
}
.primary { background: var(--vert); color: white; }
.secondary { background: var(--vert-clair); color: var(--vert); }
.warning { background: #f7e9d1; color: #704b0b; }
.actions { margin-top: 18px; }
#fiche { display: none; }
.fiche-head {
  text-align: center;
  padding: 15px;
  border: 2px solid var(--vert);
  border-radius: 10px;
  margin-bottom: 15px;
}
.fiche-head h2 { border: 0; margin: 0; }
.subtitle { font-weight: bold; color: var(--vert); }
.meta {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 8px;
  margin: 12px 0;
}
.meta div {
  background: var(--vert-clair);
  border: 1px solid var(--bordure);
  padding: 8px;
  border-radius: 6px;
  overflow-wrap: anywhere;
}
.meta strong { display: block; font-size: 12px; color: var(--vert); }
.content-block {
  border: 1px solid var(--bordure);
  border-radius: 8px;
  padding: 12px;
  margin: 10px 0;
  overflow-wrap: anywhere;
}
.content-block h3 { margin-top: 0; }
table {
  width: 100%;
  border-collapse: collapse;
  margin: 12px 0;
  font-size: 13px;
}
th, td {
  border: 1px solid #87998c;
  padding: 8px;
  vertical-align: top;
  text-align: left;
  overflow-wrap: anywhere;
}
th { background: var(--vert-clair); color: #173d25; }
.phase-title td {
  background: #e2eee5;
  color: #174d2b;
  font-weight: bold;
}
.small-note { font-size: 12px; color: #52665a; }
footer { text-align: center; padding: 20px; font-size: 12px; color: #52665a; }
@media (max-width: 600px) {
  .grid { grid-template-columns: 1fr; }
  .meta { grid-template-columns: repeat(2, minmax(0, 1fr)); }
  .panel { padding: 13px; }
  table { font-size: 11px; }
  th, td { padding: 5px; }
}
@media print {
  @page { size: A4; margin: 12mm; }
  body { background: white; color: black; font-size: 11px; }
  header, #formulaire, footer, .print-actions { display: none !important; }
  main { max-width: none; margin: 0; padding: 0; }
  #fiche { display: block !important; }
  .panel { box-shadow: none; padding: 0; margin: 0; border-radius: 0; }
  .fiche-head { border-color: black; }
  h2, h3, .subtitle { color: black; }
  .meta div, th, .phase-title td {
    background: #f1f1f1 !important;
    color: black !important;
    -webkit-print-color-adjust: exact;
    print-color-adjust: exact;
  }
  table { font-size: 9px; }
  th, td { padding: 5px; }
  .content-block { break-inside: avoid; }
  tr { break-inside: avoid; }
}
</style>
</head>
<body>

<header>
  <h1>Bot pédagogique APC Bénin</h1>
  <p>Préparer, structurer et imprimer une fiche pédagogique</p>
</header>

<main>
<section class="panel" id="formulaire">
  <h2>1. Informations générales</h2>
  <form id="form">
    <div class="grid">
      <div class="field">
        <label for="ecole">École</label>
        <input id="ecole" placeholder="Nom de l'école">
      </div>
      <div class="field">
        <label for="enseignant">Nom de l'enseignant(e)</label>
        <input id="enseignant" placeholder="Nom complet">
      </div>
      <div class="field">
        <label for="classe">Cours</label>
        <select id="classe">
          <option>CI</option><option>CP</option><option>CE1</option>
          <option>CE2</option><option>CM1</option><option>CM2</option>
        </select>
      </div>
      <div class="field">
        <label for="discipline">Discipline</label>
        <select id="discipline">
          <option>Français</option>
          <option>Mathématiques</option>
          <option>Éducation sociale - Morale</option>
          <option>Éducation sociale - Civisme</option>
          <option>Éducation sociale - Histoire</option>
          <option>Éducation sociale - Géographie</option>
          <option>Éducation sociale - Langues et culture</option>
          <option>EST</option>
          <option>Éducation artistique - Dessin</option>
          <option>Éducation artistique - Chant</option>
          <option>Éducation artistique - Travaux manuels</option>
          <option>Éducation artistique - Poésie</option>
          <option>Éducation artistique - Conte</option>
          <option>Éducation artistique - Couture</option>
          <option>EPS</option>
        </select>
      </div>
      <div class="field">
        <label for="type">Type de document</label>
        <select id="type">
          <option>Fiche de préparation complète</option>
          <option>Résumé de cours</option>
        </select>
      </div>
      <div class="field">
        <label for="date">Date</label>
        <input id="date" type="date">
      </div>
      <div class="field">
        <label for="periode">Période / séquence d'apprentissage</label>
        <input id="periode" placeholder="Ex. : 2e période">
      </div>
      <div class="field">
        <label for="mois">Mois</label>
        <input id="mois" placeholder="Ex. : octobre">
      </div>
      <div class="field">
        <label for="semaine">Semaine</label>
        <input id="semaine" placeholder="Ex. : semaine 3">
      </div>
      <div class="field">
        <label for="seance">Séance</label>
        <input id="seance" placeholder="Ex. : séance 1">
      </div>
      <div class="field">
        <label for="duree">Durée totale (minutes)</label>
        <input id="duree" type="number" min="5" value="30" required>
      </div>
    </div>

    <h2 style="margin-top:25px">2. Préparation pédagogique</h2>
    <div class="grid">
      <div class="field full">
        <label for="titre">Titre / notion à enseigner *</label>
        <input id="titre" placeholder="Ex. : Les diphtongues" required>
      </div>
      <div class="field full">
        <label for="theme">Thème</label>
        <input id="theme" placeholder="Thème de la leçon">
      </div>
      <div class="field full">
        <label for="competence">Compétence disciplinaire visée</label>
        <textarea id="competence" placeholder="Compétence à développer chez l'apprenant"></textarea>
      </div>
      <div class="field full">
        <label for="tvctd">Compétence transversale / TV-CTD</label>
        <textarea id="tvctd" placeholder="Compétence transversale, si applicable"></textarea>
      </div>
      <div class="field full">
        <label for="connaissances">Connaissances et techniques</label>
        <textarea id="connaissances" placeholder="Notions, techniques ou savoir-faire"></textarea>
      </div>
      <div class="field full">
        <label for="prerequis">Prérequis / acquis antérieurs</label>
        <textarea id="prerequis" placeholder="Ce que les apprenants doivent déjà connaître"></textarea>
      </div>
      <div class="field full">
        <label for="objectif">Objectif d'apprentissage</label>
        <textarea id="objectif" placeholder="À la fin de la séance, l'apprenant sera capable de..."></textarea>
      </div>
      <div class="field full">
        <label for="situation">Situation d'apprentissage / mise en situation</label>
        <textarea id="situation" placeholder="Situation concrète proposée aux apprenants"></textarea>
      </div>
      <div class="field full">
        <label for="strategies">Stratégies d'enseignement, d'apprentissage et d'évaluation</label>
        <textarea id="strategies" placeholder="Ex. : observation, travail individuel, travail en groupe, exercices"></textarea>
      </div>
      <div class="field full">
        <label for="materiel">Matériel / supports didactiques</label>
        <textarea id="materiel" placeholder="Tableau, images, objets, ardoises, fiches..."></textarea>
      </div>
    </div>

    <h2 style="margin-top:25px">3. Consignes et résultats attendus</h2>
    <p class="small-note">Complète les étapes utiles à ta leçon. Les durées proposées sont indicatives et peuvent être adaptées.</p>
    <div class="grid">
      <div class="field full">
        <label for="motivation">Phase préliminaire / motivation</label>
        <textarea id="motivation" placeholder="Consigne, activité ou question de départ"></textarea>
      </div>
      <div class="field full">
        <label for="intro">Introduction : mise en situation et mobilisation des acquis</label>
        <textarea id="intro" placeholder="Questions, consignes, rappel des prérequis"></textarea>
      </div>
      <div class="field full">
        <label for="decouverte">Réalisation : découverte et recherche</label>
        <textarea id="decouverte" placeholder="Tâches à réaliser, recherche individuelle ou en groupe"></textarea>
      </div>
      <div class="field full">
        <label for="construction">Construction et structuration des savoirs</label>
        <textarea id="construction" placeholder="Explication, mise en commun, règle ou trace écrite"></textarea>
      </div>
      <div class="field full">
        <label for="application">Application / entraînement</label>
        <textarea id="application" placeholder="Exercices, manipulation ou mise en pratique"></textarea>
      </div>
      <div class="field full">
        <label for="evaluation">Évaluation des apprentissages</label>
        <textarea id="evaluation" placeholder="Questions ou tâches permettant de vérifier les acquis"></textarea>
      </div>
      <div class="field full">
        <label for="resultats">Résultats attendus / productions des apprenants</label>
        <textarea id="resultats" placeholder="Ce que les apprenants doivent dire, faire, produire ou réussir"></textarea>
      </div>
      <div class="field full">
        <label for="remediation">Remédiation prévue</label>
        <textarea id="remediation" placeholder="Aide proposée en cas de difficulté"></textarea>
      </div>
      <div class="field full">
        <label for="projection">Retour, objectivation et projection</label>
        <textarea id="projection" placeholder="Bilan de la séance et annonce de la suite"></textarea>
      </div>
      <div class="field full">
        <label for="notes">Notes personnelles de l'enseignant(e)</label>
        <textarea id="notes" placeholder="Durée réelle, difficultés rencontrées, suggestions"></textarea>
      </div>
    </div>

    <div class="actions">
      <button class="primary" type="submit">Générer la fiche</button>
      <button class="secondary" type="reset">Effacer le formulaire</button>
    </div>
  </form>
</section>

<section class="panel" id="fiche">
  <div id="contenuFiche"></div>
  <div class="print-actions">
    <button class="primary" type="button" onclick="window.print()">Imprimer / Enregistrer en PDF</button>
    <button class="secondary" type="button" onclick="modifier()">Modifier la fiche</button>
  </div>
</section>
</main>

<footer>Bot pédagogique APC Bénin — Outil d'aide à la préparation. Vérifier les contenus avec les documents pédagogiques de référence.</footer>

<script>
const $ = id => document.getElementById(id);
const valeur = id => $(id).value.trim();
const echapper = texte => String(texte || "").replace(/[&<>"']/g, c => ({
  "&":"&amp;", "<":"&lt;", ">":"&gt;", '"':"&quot;", "'":"&#39;"
}[c]));
const afficher = texte => echapper(texte).replace(/\n/g, "<br>");

function bloc(titre, texte) {
  if (!texte) return "";
  return `<section class="content-block"><h3>${echapper(titre)}</h3><div>${afficher(texte)}</div></section>`;
}

function cellule(titre, texte) {
  return `<div><strong>${echapper(titre)}</strong>${afficher(texte || "Non renseigné")}</div>`;
}

function ligne(phase, duree, consignes, resultats) {
  return `<tr>
    <td>${echapper(phase)}<br><strong>${duree} min</strong></td>
    <td>${afficher(consignes || "À préciser selon la leçon.")}</td>
    <td>${afficher(resultats || "Les apprenants participent et réalisent la tâche demandée.")}</td>
  </tr>`;
}

$("form").addEventListener("submit", function(e) {
  e.preventDefault();
  const total = Number(valeur("duree"));
  if (!total || total < 5) {
    alert("Indique une durée totale d'au moins 5 minutes.");
    return;
  }

  const phases = [
    ["PHASES PRÉLIMINAIRES", [
      ["Motivation et préparation", valeur("motivation"), "Les apprenants se préparent et s'intéressent à la situation."]
    ]],
    ["INTRODUCTION", [
      ["Mise en situation et acquis antérieurs", valeur("intro"), "Les apprenants mobilisent leurs acquis et comprennent la tâche."]
    ]],
    ["RÉALISATION", [
      ["Découverte et recherche", valeur("decouverte"), "Les apprenants observent, recherchent, proposent et confrontent leurs idées."],
      ["Construction et structuration", valeur("construction"), "Les apprenants formulent ou retiennent les savoirs essentiels."],
      ["Application et entraînement", valeur("application"), "Les apprenants appliquent les apprentissages à une tâche."]
    ]],
    ["RETOUR ET PROJECTION", [
      ["Évaluation", valeur("evaluation"), valeur("resultats") || "Les acquis sont vérifiés à partir des réponses et productions."],
      ["Objectivation et projection", valeur("projection"), "Les apprenants font le bilan et se préparent à la suite."]
    ]]
  ];

  // Répartition indicative du temps entre les étapes.
  const poids = [15, 15, 20, 20, 15, 10, 5];
  let durees = poids.map(p => Math.floor(total * p / 100));
  let reste = total - durees.reduce((a,b) => a+b, 0);
  for (let i=0; i<reste; i++) durees[i % durees.length]++;

  const lignes = [
    ["PHASES PRÉLIMINAIRES", "Motivation et préparation", valeur("motivation"), "Les apprenants se préparent et s'intéressent à la situation.", durees[0]],
    ["INTRODUCTION", "Mise en situation et acquis antérieurs", valeur("intro"), "Les apprenants mobilisent leurs acquis et comprennent la tâche.", durees[1]],
    ["RÉALISATION", "Découverte et recherche", valeur("decouverte"), "Les apprenants observent, recherchent, proposent et confrontent leurs idées.", durees[2]],
    ["RÉALISATION", "Construction et structuration", valeur("construction"), "Les apprenants formulent ou retiennent les savoirs essentiels.", durees[3]],
    ["RÉALISATION", "Application et entraînement", valeur("application"), "Les apprenants appliquent les apprentissages à une tâche.", durees[4]],
    ["RETOUR ET PROJECTION", "Évaluation", valeur("evaluation"), valeur("resultats") || "Les acquis sont vérifiés à partir des réponses et productions.", durees[5]],
    ["RETOUR ET PROJECTION", "Objectivation et projection", valeur("projection"), "Les apprenants font le bilan et se préparent à la suite.", durees[6]]
  ];

  let tableau = "";
  let sectionActuelle = "";
  lignes.forEach(p => {
    if (p[0] !== sectionActuelle) {
      sectionActuelle = p[0];
      tableau += `<tr class="phase-title"><td colspan="3">${echapper(sectionActuelle)}</td></tr>`;
    }
    tableau += ligne(p[1], p[5], p[2], p[3]);
  });

  const date = valeur("date");
  const dateAffichee = date ? new Date(date + "T12:00:00").toLocaleDateString("fr-FR") : "Non renseignée";
  const titre = valeur("titre");

  $("contenuFiche").innerHTML = `
    <div class="fiche-head">
      <h2>FICHE DE PRÉPARATION PÉDAGOGIQUE</h2>
      <div class="subtitle">Approche par compétences — Bénin</div>
      <p>${afficher(titre)}</p>
    </div>

    <div class="meta">
      ${cellule("École", valeur("ecole"))}
      ${cellule("Enseignant(e)", valeur("enseignant"))}
      ${cellule("Cours", valeur("classe"))}
      ${cellule("Discipline", valeur("discipline"))}
      ${cellule("Type de document", valeur("type"))}
      ${cellule("Durée totale", total + " minutes")}
      ${cellule("Date", dateAffichee)}
      ${cellule("Période / séquence", valeur("periode"))}
      ${cellule("Mois", valeur("mois"))}
      ${cellule("Semaine", valeur("semaine"))}
      ${cellule("Séance", valeur("seance"))}
      ${cellule("Thème", valeur("theme"))}
    </div>

    ${bloc("COMPÉTENCE DISCIPLINAIRE", valeur("competence"))}
    ${bloc("COMPÉTENCE TRANSVERSALE / TV-CTD", valeur("tvctd"))}
    ${bloc("CONNAISSANCES ET TECHNIQUES", valeur("connaissances"))}
    ${bloc("PRÉREQUIS / ACQUIS ANTÉRIEURS", valeur("prerequis"))}
    ${bloc("OBJECTIF D'APPRENTISSAGE", valeur("objectif"))}
    ${bloc("SITUATION D'APPRENTISSAGE", valeur("situation"))}
    ${bloc("STRATÉGIES PÉDAGOGIQUES", valeur("strategies"))}
    ${bloc("MATÉRIEL ET SUPPORTS DIDACTIQUES", valeur("materiel"))}

    <h3 style="text-align:center;margin-top:22px">DÉROULEMENT DE LA SÉANCE</h3>
    <table>
      <thead><tr>
        <th style="width:22%">PHASES / ÉTAPES</th>
        <th style="width:39%">CONSIGNES / ACTIVITÉS</th>
        <th style="width:39%">RÉSULTATS ATTENDUS</th>
      </tr></thead>
      <tbody>${tableau}</tbody>
    </table>

    ${bloc("REMÉDIATION", valeur("remediation"))}
    ${bloc("NOTES PERSONNELLES DE L'ENSEIGNANT(E)", valeur("notes"))}
    <p class="small-note">Document généré à partir des informations saisies. Adapter les étapes, les durées, les consignes et les résultats attendus à la discipline et aux documents de référence.</p>
  `;

  $("fiche").style.display = "block";
  $("fiche").scrollIntoView({behavior:"smooth", block:"start"});
});

function modifier() {
  $("formulaire").scrollIntoView({behavior:"smooth", block:"start"});
}

$("form").addEventListener("reset", function() {
  setTimeout(() => {
    $("fiche").style.display = "none";
    $("contenuFiche").innerHTML = "";
  }, 0);
});
</script>
</body>
</html>
