
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
  background: white;
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
  font-size: 12px;
  table-layout: fixed;
}
th, td {
  border: 1px solid #87998c;
  padding: 7px;
  vertical-align: top;
  text-align: left;
  overflow-wrap: anywhere;
  word-break: normal;
}
th { background: var(--vert-clair); color: #173d25; }
.phase-title td {
  background: #e2eee5;
  color: #174d2b;
  font-weight: bold;
}
.small-note { font-size: 12px; color: #52665a; }
footer { text-align: center; padding: 20px; font-size: 12px; color: #52665a; }

@media (max-width: 700px) {
  .grid { grid-template-columns: 1fr; }
  .meta { grid-template-columns: repeat(2, minmax(0, 1fr)); }
  .panel { padding: 13px; }
  .table-wrap { overflow-x: auto; }
  table { min-width: 850px; font-size: 12px; }
}

@media print {
  @page { size: A4 landscape; margin: 10mm; }
  body { background: white; color: black; font-size: 10px; }
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
  table { font-size: 8px; table-layout: fixed; }
  th, td { padding: 4px; overflow-wrap: anywhere; }
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
        <input id="duree" type="number" min="7" value="30" required>
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
        <textarea id="strategies" placeholder="Observation, travail individuel, travail en groupe, exercices..."></textarea>
      </div>
      <div class="field full">
        <label for="materiel">Matériel / supports didactiques</label>
        <textarea id="materiel" placeholder="Tableau, images, objets, ardoises, fiches..."></textarea>
      </div>
    </div>

    <h2 style="margin-top:25px">3. Consignes et résultats attendus</h2>
    <p class="small-note">
      Les propositions automatiques sont indicatives. Tu peux saisir tes propres consignes pour chaque étape.
    </p>

    <div class="grid">
      <div class="field full">
        <label for="motivation">Phase préliminaire / motivation</label>
        <textarea id="motivation" placeholder="Consigne ou question de départ"></textarea>
      </div>
      <div class="field full">
        <label for="intro">Introduction : mise en situation et acquis antérieurs</label>
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

<footer>
  Bot pédagogique APC Bénin — Outil d'aide à la préparation.
  Vérifier les contenus avec les documents pédagogiques de référence.
</footer>

<script>
"use strict";

const $ = id => document.getElementById(id);
const valeur = id => $(id).value.trim();

const echapper = texte => String(texte || "").replace(/[&<>"']/g, c => ({
  "&": "&amp;",
  "<": "&lt;",
  ">": "&gt;",
  '"': "&quot;",
  "'": "&#39;"
}[c]));

const afficher = texte => echapper(texte).replace(/\n/g, "<br>");

function bloc(titre, texte) {
  if (!texte) return "";
  return `<section class="content-block">
    <h3>${echapper(titre)}</h3>
    <div>${afficher(texte)}</div>
  </section>`;
}

function cellule(titre, texte) {
  return `<div><strong>${echapper(titre)}</strong>${afficher(texte || "Non renseigné")}</div>`;
}

/* Suggestions générales par grande famille de disciplines.
   Ces propositions doivent être adaptées à la notion et au programme. */
const profils = {
  francais: {
    decouverte: "Présenter des mots, phrases, textes ou supports liés à la notion. Demander aux apprenants d'observer, de lire ou d'écouter.",
    apprenants: "Observer les supports, lire ou écouter, relever les éléments utiles et formuler des hypothèses.",
    construction: "Faire comparer les réponses, guider la formulation de la règle ou de la notion, puis faire produire une trace écrite.",
    application: "Proposer des exercices oraux et écrits progressifs, puis une tâche de réinvestissement.",
    evaluation: "Vérifier que les apprenants reconnaissent la notion et savent l'utiliser dans un exemple nouveau.",
    resultat: "Les apprenants identifient la notion étudiée, expliquent leur démarche et réalisent correctement les exercices."
  },
  mathematiques: {
    decouverte: "Présenter une situation-problème, du matériel concret, des figures, des nombres ou des mesures adaptés à la notion.",
    apprenants: "Manipuler, observer, compter, mesurer, tracer, calculer ou rechercher une solution individuellement ou en groupe.",
    construction: "Faire expliquer les démarches, comparer les stratégies et établir la règle, la propriété ou la technique.",
    application: "Proposer des exercices gradués et un problème de transfert dans une situation concrète.",
    evaluation: "Donner un exercice ou un problème permettant de vérifier la procédure et la justesse du résultat.",
    resultat: "Les apprenants choisissent une démarche pertinente, justifient leur réponse et obtiennent un résultat vérifiable."
  },
  social: {
    decouverte: "Présenter une situation de vie, une image, un récit, un document ou un problème social en lien avec la leçon.",
    apprenants: "Observer, décrire, raconter, comparer les situations et exprimer leurs idées en respectant les autres.",
    construction: "Guider les échanges, clarifier les faits et faire dégager les valeurs, règles ou connaissances essentielles.",
    application: "Proposer une étude de cas, un jeu de rôle, un classement ou une action adaptée au thème.",
    evaluation: "Poser des questions de compréhension et proposer une situation où l'apprenant applique ce qu'il a appris.",
    resultat: "Les apprenants expliquent les notions essentielles et proposent une conduite ou une solution adaptée."
  },
  est: {
    decouverte: "Présenter un objet, un phénomène, un outil, une image ou une situation d'observation en lien avec la leçon.",
    apprenants: "Observer, décrire, questionner, manipuler avec prudence et relever les informations utiles.",
    construction: "Comparer les observations, expliquer le phénomène ou la technique et établir les étapes essentielles.",
    application: "Faire réaliser une expérience simple, une démonstration, un montage ou une tâche pratique adaptée.",
    evaluation: "Vérifier la compréhension, le respect des étapes, la sécurité et la qualité de la réalisation.",
    resultat: "Les apprenants décrivent le phénomène ou réalisent la tâche en respectant les consignes de sécurité."
  },
  artistique: {
    decouverte: "Présenter un modèle, une œuvre, un rythme, un chant, un texte ou le matériel nécessaire à la production.",
    apprenants: "Écouter, observer, répéter, expérimenter les gestes ou techniques et exprimer leurs impressions.",
    construction: "Démontrer les gestes ou techniques, guider les essais et faire repérer les critères d'une réalisation réussie.",
    application: "Faire répéter, interpréter, dessiner, fabriquer ou réaliser une production selon la discipline choisie.",
    evaluation: "Observer la participation, la maîtrise de la technique, le respect des consignes et la production obtenue.",
    resultat: "Les apprenants présentent une réalisation ou une interprétation correspondant aux critères annoncés."
  },
  eps: {
    decouverte: "Présenter l'objectif moteur, aménager l'espace et expliquer les règles et les consignes de sécurité.",
    apprenants: "Écouter, observer la démonstration, s'échauffer puis essayer les mouvements ou situations proposés.",
    construction: "Démontrer le geste, décomposer les étapes et corriger les mouvements avec des conseils adaptés.",
    application: "Organiser des ateliers, des répétitions ou des jeux adaptés au niveau des apprenants.",
    evaluation: "Observer l'exécution du geste, le respect des règles, la progression et la sécurité.",
    resultat: "Les apprenants réalisent le mouvement ou la tâche motrice en respectant les règles et les consignes."
  }
};

function profilActuel() {
  const discipline = valeur("discipline");

  if (discipline === "Mathématiques") return profils.mathematiques;
  if (discipline === "EST") return profils.est;
  if (discipline === "EPS") return profils.eps;
  if (discipline.startsWith("Éducation artistique")) return profils.artistique;
  if (discipline.startsWith("Éducation sociale")) return profils.social;

  return profils.francais;
}

function suggestionEnseignant(phase, profil) {
  const suggestions = {
    "Motivation et préparation":
      "Présenter une situation d'entrée en lien avec la notion et annoncer la tâche à réaliser.",
    "Mise en situation et acquis antérieurs":
      "Poser des questions de rappel, présenter la situation-problème et recueillir les réponses.",
    "Découverte et recherche": profil.decouverte,
    "Construction et structuration": profil.construction,
    "Application et entraînement": profil.application,
    "Évaluation": profil.evaluation,
    "Objectivation et projection":
      "Demander aux apprenants ce qu'ils ont retenu, relever les difficultés et annoncer la suite."
  };

  return suggestions[phase] || "Donner une consigne claire et observer les démarches des apprenants.";
}

function suggestionApprenants(phase, profil) {
  const suggestions = {
    "Motivation et préparation":
      "Écouter, observer et se préparer à participer.",
    "Mise en situation et acquis antérieurs":
      "Rappeler les acquis, répondre aux questions et comprendre le problème posé.",
    "Découverte et recherche": profil.apprenants,
    "Construction et structuration":
      "Expliquer les démarches, comparer les réponses et retenir l'essentiel.",
    "Application et entraînement":
      "Réaliser les exercices, appliquer la notion et corriger les erreurs.",
    "Évaluation":
      "Répondre individuellement aux questions et produire le travail demandé.",
    "Objectivation et projection":
      "Dire ce qui a été appris et identifier ce qui reste à améliorer."
  };

  return suggestions[phase] || "Participer à la tâche et présenter sa production.";
}

function suggestionResultat(phase, profil) {
  const resultats = {
    "Motivation et préparation":
      "Les apprenants sont attentifs et comprennent la situation proposée.",
    "Mise en situation et acquis antérieurs":
      "Les acquis utiles sont rappelés et le problème à résoudre est compris.",
    "Découverte et recherche": profil.resultat,
    "Construction et structuration":
      "Les apprenants formulent ou retiennent les savoirs essentiels de la leçon.",
    "Application et entraînement":
      "Les apprenants appliquent la notion à des tâches adaptées à leur niveau.",
    "Évaluation": profil.resultat,
    "Objectivation et projection":
      "Les apprenants expriment l'essentiel retenu et identifient la prochaine étape."
  };

  return resultats[phase] || "Les apprenants réalisent la tâche demandée.";
}

function repartitionDurees(total, poids) {
  const durees = poids.map(p => Math.floor(total * p / 100));
  let reste = total - durees.reduce((a, b) => a + b, 0);

  for (let i = 0; i < reste; i++) {
    durees[i % durees.length]++;
  }

  /* Si la séance est assez longue, éviter les étapes de durée nulle. */
  if (total >= poids.length) {
    for (let i = 0; i < durees.length; i++) {
      if (durees[i] === 0) {
        const donneur = durees.findIndex((d, j) => d > 1 && j !== i);
        if (donneur >= 0) {
          durees[donneur]--;
          durees[i] = 1;
        }
      }
    }
  }

  return durees;
}

$("form").addEventListener("submit", function(e) {
  e.preventDefault();

  const total = Number(valeur("duree"));

  if (!valeur("titre")) {
    alert("Saisis le titre de la leçon.");
    $("titre").focus();
    return;
  }

  if (!Number.isFinite(total) || total < 7) {
    alert("Indique une durée totale d'au moins 7 minutes.");
    $("duree").focus();
    return;
  }

  const profil = profilActuel();

  const etapes = [
    {
      section: "PHASES PRÉLIMINAIRES",
      phase: "Motivation et préparation",
      id: "motivation",
      poids: 10
    },
    {
      section: "INTRODUCTION",
      phase: "Mise en situation et acquis antérieurs",
      id: "intro",
      poids: 15
    },
    {
      section: "RÉALISATION",
      phase: "Découverte et recherche",
      id: "decouverte",
      poids: 20
    },
    {
      section: "RÉALISATION",
      phase: "Construction et structuration",
      id: "construction",
      poids: 20
    },
    {
      section: "RÉALISATION",
      phase: "Application et entraînement",
      id: "application",
      poids: 15
    },
    {
      section: "RETOUR ET PROJECTION",
      phase: "Évaluation",
      id: "evaluation",
      poids: 15
    },
    {
      section: "RETOUR ET PROJECTION",
      phase: "Objectivation et projection",
      id: "projection",
      poids: 5
    }
  ];

  const durees = repartitionDurees(total, etapes.map(e => e.poids));

  let tableau = "";
  let sectionActuelle = "";

  etapes.forEach((etape, index) => {
    if (etape.section !== sectionActuelle) {
      sectionActuelle = etape.section;
      tableau += `<tr class="phase-title">
        <td colspan="5">${echapper(sectionActuelle)}</td>
      </tr>`;
    }

    const consigne =
      valeur(etape.id) || suggestionEnseignant(etape.phase, profil);

    const activites = suggestionApprenants(etape.phase, profil);

    let resultat = suggestionResultat(etape.phase, profil);

    /* Les résultats saisis par l'enseignant sont utilisés dans la phase
       d'évaluation, et restent affichés dans un bloc dédié plus bas. */
    if (etape.phase === "Évaluation" && valeur("resultats")) {
      resultat = valeur("resultats");
    }

    const evaluation = etape.phase === "Évaluation"
      ? (valeur("evaluation") || profil.evaluation)
      : "Observer les démarches, les réponses et les productions.";

    tableau += `<tr>
      <td>${echapper(etape.phase)}<br><strong>${durees[index]} min</strong></td>
      <td>${afficher(consigne)}</td>
      <td>${afficher(activites)}</td>
      <td>${afficher(resultat)}</td>
      <td>${afficher(evaluation)}</td>
    </tr>`;
  });

  const date = valeur("date");
  const dateAffichee = date
    ? new Date(date + "T12:00:00").toLocaleDateString("fr-FR")
    : "Non renseignée";

  $("contenuFiche").innerHTML = `
    <div class="fiche-head">
      <h2>FICHE DE PRÉPARATION PÉDAGOGIQUE</h2>
      <div class="subtitle">Approche par compétences — Bénin</div>
      <p><strong>${afficher(valeur("titre"))}</strong></p>
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

    <h3 style="text-align:center;margin-top:22px">
      DÉROULEMENT DE LA SÉANCE
    </h3>

    <div class="table-wrap">
      <table>
        <colgroup>
          <col style="width:17%">
          <col style="width:23%">
          <col style="width:23%">
          <col style="width:19%">
          <col style="width:18%">
        </colgroup>
        <thead>
          <tr>
            <th>PHASE / DURÉE</th>
            <th>CONSIGNES ET ACTIVITÉS DE L'ENSEIGNANT</th>
            <th>ACTIVITÉS DES APPRENANTS</th>
            <th>RÉSULTATS ATTENDUS</th>
            <th>ÉVALUATION / OBSERVATION</th>
          </tr>
        </thead>
        <tbody>${tableau}</tbody>
      </table>
    </div>

    ${bloc("RÉSULTATS ATTENDUS / PRODUCTIONS DES APPRENANTS", valeur("resultats"))}
    ${bloc("REMÉDIATION", valeur("remediation"))}
    ${bloc("RETOUR, OBJECTIVATION ET PROJECTION", valeur("projection"))}
    ${bloc("NOTES PERSONNELLES DE L'ENSEIGNANT(E)", valeur("notes"))}

    <p class="small-note">
      Les propositions automatiques sont indicatives. Adapter les contenus,
      les étapes, les durées et les critères au programme, à la discipline,
      au niveau de la classe et aux documents pédagogiques de référence.
    </p>
  `;

  $("fiche").style.display = "block";
  $("fiche").scrollIntoView({ behavior: "smooth", block: "start" });
});

function modifier() {
  $("formulaire").scrollIntoView({ behavior: "smooth", block: "start" });
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
