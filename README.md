
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bot pédagogique APC Bénin</title>

<style>
:root {
  --vert: #176534;
  --vert-clair: #eaf5ed;
  --bordure: #cbd8ce;
  --texte: #203328;
}
* { box-sizing: border-box; }
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f0f5f1;
  color: var(--texte);
  line-height: 1.5;
}
header {
  background: var(--vert);
  color: white;
  text-align: center;
  padding: 22px 12px;
}
header h1 { margin: 0 0 6px; font-size: 24px; }
header p { margin: 0; }
main {
  width: min(960px, 94%);
  margin: 20px auto;
}
.panel, #fiche {
  background: white;
  border: 1px solid var(--bordure);
  border-radius: 10px;
  padding: 18px;
  margin-bottom: 20px;
}
h2, h3 { color: var(--vert); }
h2 { margin-top: 0; }
.form-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 14px;
}
label {
  display: block;
  font-weight: bold;
  margin-bottom: 5px;
}
input, select, textarea {
  width: 100%;
  padding: 11px;
  border: 1px solid #aabbb0;
  border-radius: 6px;
  font: inherit;
  background: white;
}
textarea { min-height: 75px; resize: vertical; }
button {
  border: 0;
  border-radius: 6px;
  padding: 12px 16px;
  margin: 8px 6px 0 0;
  background: var(--vert);
  color: white;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
}
button.secondary { background: #56665c; }
button.print { background: #145b9a; }
#fiche { display: none; }
.fiche-entete {
  text-align: center;
  border-bottom: 2px solid var(--vert);
  padding-bottom: 12px;
}
.fiche-entete h2 { margin-bottom: 4px; }
.info {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 8px;
  margin: 15px 0;
}
.info div {
  background: var(--vert-clair);
  padding: 9px;
  border-radius: 5px;
  overflow-wrap: anywhere;
}
.phase {
  border: 1px solid var(--bordure);
  border-radius: 6px;
  padding: 12px;
  margin: 12px 0;
  break-inside: avoid;
}
.phase h3 { margin-top: 0; }
table {
  width: 100%;
  border-collapse: collapse;
  margin: 12px 0;
}
th, td {
  border: 1px solid #9ba99f;
  padding: 8px;
  text-align: left;
  vertical-align: top;
}
th { background: var(--vert-clair); }
.notice { font-size: 14px; color: #526258; }
.actions { margin-top: 14px; }
@media print {
  body { background: white; color: black; font-size: 11pt; }
  header, #formulaire, .actions, .notice { display: none !important; }
  main { width: 100%; margin: 0; }
  #fiche {
    display: block !important;
    border: 0;
    padding: 0;
    margin: 0;
  }
  .phase, .info div { break-inside: avoid; }
  button { display: none !important; }
}
</style>
</head>

<body>
<header>
  <h1>Bot pédagogique APC Bénin</h1>
  <p>Préparation des leçons selon l’Approche Par Compétences</p>
</header>

<main>
<section class="panel" id="formulaire">
  <h2>Préparer une leçon</h2>
  <p>Remplis les champs ci-dessous, puis appuie sur « Générer le document ».</p>

  <div class="form-grid">
    <div>
      <label for="classe">Classe</label>
      <select id="classe">
        <option value="CI">CI</option>
        <option value="CP">CP</option>
        <option value="CE1" selected>CE1</option>
        <option value="CE2">CE2</option>
        <option value="CM1">CM1</option>
        <option value="CM2">CM2</option>
      </select>
    </div>

    <div>
      <label for="discipline">Discipline</label>
      <select id="discipline">
        <option>Français</option>
        <option>Mathématiques - Arithmétique</option>
        <option>Mathématiques - Géométrie</option>
        <option>Mathématiques - Mesures</option>
        <option>Éducation Sociale - Morale</option>
        <option>Éducation Sociale - Civisme</option>
        <option>Histoire</option>
        <option>Géographie</option>
        <option>Langues et culture</option>
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
      <label for="effectif">Effectif de la classe</label>
      <input id="effectif" type="number" min="1" placeholder="Ex. : 35">
    </div>

    <div>
      <label for="objectif">Objectif d’apprentissage</label>
      <textarea id="objectif" placeholder="Ce que l’apprenant devra savoir ou savoir faire."></textarea>
    </div>

    <div>
      <label for="materiel">Matériel / supports</label>
      <textarea id="materiel" placeholder="Tableau, ardoises, images, manuel..."></textarea>
    </div>

    <div>
      <label for="prerequis">Prérequis</label>
      <textarea id="prerequis" placeholder="Connaissances déjà acquises par les apprenants."></textarea>
    </div>

    <div>
      <label for="competence">Compétence visée</label>
      <textarea id="competence" placeholder="Compétence à développer chez l’apprenant."></textarea>
    </div>

    <div>
      <label for="resultats">Résultats attendus</label>
      <textarea id="resultats" placeholder="À la fin, l’apprenant sera capable de..."></textarea>
    </div>

    <div>
      <label for="consigne">Consigne principale</label>
      <textarea id="consigne" placeholder="Travail demandé aux apprenants."></textarea>
    </div>

    <div>
      <label for="evaluation">Évaluation / exercice d’application</label>
      <textarea id="evaluation" placeholder="Questions ou tâches pour vérifier les acquis."></textarea>
    </div>

    <div>
      <label for="enseignant">Nom de l’enseignant (facultatif)</label>
      <input id="enseignant" placeholder="Nom et prénom">
    </div>
  </div>

  <div class="actions">
    <button type="button" onclick="generer()">Générer le document</button>
    <button type="button" class="secondary" onclick="reinitialiser()">Effacer les champs</button>
  </div>

  <p class="notice">
    Le document généré est une trame pédagogique à adapter au programme officiel
    et aux documents de référence de la classe.
  </p>
</section>

<section id="fiche">
  <div class="fiche-entete">
    <h2>FICHE DE PRÉPARATION PÉDAGOGIQUE</h2>
    <p>Approche Par Compétences (APC) — Bénin</p>
  </div>

  <div id="contenuFiche"></div>

  <div class="actions">
    <button type="button" class="print" onclick="window.print()">Imprimer / Enregistrer en PDF</button>
    <button type="button" class="secondary" onclick="modifierFiche()">Modifier la préparation</button>
  </div>
</section>
</main>

<script>
function valeur(id) {
  return document.getElementById(id).value.trim();
}

function echapper(texte) {
  return String(texte).replace(/[&<>"']/g, function(c) {
    return {
      "&": "&amp;",
      "<": "&lt;",
      ">": "&gt;",
      '"': "&quot;",
      "'": "&#39;"
    }[c];
  });
}

function afficher(texte, defaut) {
  return echapper(texte || defaut || "À compléter.");
}

function generer() {
  const notion = valeur("notion");

  if (!notion) {
    alert("Veuillez saisir le titre ou la notion de la leçon.");
    document.getElementById("notion").focus();
    return;
  }

  const duree = valeur("duree") || "30";
  const classe = valeur("classe");
  const discipline = valeur("discipline");

  const donnees = {
    semaine: valeur("semaine"),
    effectif: valeur("effectif"),
    objectif: valeur("objectif"),
    materiel: valeur("materiel"),
    prerequis: valeur("prerequis"),
    competence: valeur("competence"),
    resultats: valeur("resultats"),
    consigne: valeur("consigne"),
    evaluation: valeur("evaluation"),
    enseignant: valeur("enseignant")
  };

  const phases = [
    {
      titre: "1. Mise en situation / motivation",
      temps: "10 %",
      activite: "L’enseignant présente une situation concrète en rapport avec la notion, suscite l’intérêt et fait exprimer les idées initiales.",
      apprenant: "Les apprenants observent, écoutent, réagissent et proposent leurs premières réponses.",
      trace: "Situation de départ et réponses initiales."
    },
    {
      titre: "2. Exploration / recherche",
      temps: "20 %",
      activite: "L’enseignant présente les supports, donne une consigne claire, organise le travail individuel ou en groupes et accompagne la recherche.",
      apprenant: "Les apprenants observent les supports, manipulent, cherchent, comparent et proposent des solutions.",
      trace: "Observations, essais et propositions des apprenants."
    },
    {
      titre: "3. Mise en commun",
      temps: "20 %",
      activite: "L’enseignant invite les groupes à présenter leurs résultats, organise les échanges et demande de justifier les réponses.",
      apprenant: "Les apprenants présentent leurs démarches, expliquent leurs réponses et confrontent leurs idées.",
      trace: "Résultats des groupes et justifications."
    },
    {
      titre: "4. Structuration / synthèse",
      temps: "20 %",
      activite: "L’enseignant guide la correction, fait ressortir les notions essentielles et construit une synthèse claire avec la classe.",
      apprenant: "Les apprenants formulent la règle ou la conclusion et la consignent dans leur cahier.",
      trace: "Résumé ou règle à retenir."
    },
    {
      titre: "5. Application / entraînement",
      temps: "20 %",
      activite: "L’enseignant propose des exercices progressifs, observe les démarches et apporte une aide adaptée.",
      apprenant: "Les apprenants réalisent les exercices seuls ou en groupes et expliquent leurs démarches.",
      trace: "Exercices d’application corrigés."
    },
    {
      titre: "6. Évaluation et remédiation",
      temps: "10 %",
      activite: "L’enseignant vérifie l’atteinte des résultats attendus, relève les difficultés et prévoit des activités de remédiation.",
      apprenant: "Les apprenants répondent individuellement aux questions et corrigent leurs erreurs avec accompagnement.",
      trace: "Résultats de l’évaluation et difficultés à reprendre."
    }
  ];

  const total = Number(duree);
  let tempsRestant = total;
  const pourcentages = [10, 20, 20, 20, 20, 10];

  const phasesHTML = phases.map(function(p, i) {
    let minutes;
    if (i === phases.length - 1) {
      minutes = tempsRestant;
    } else {
      minutes = Math.round(total * pourcentages[i] / 100);
      tempsRestant -= minutes;
    }

    return `
      <div class="phase">
        <h3>${p.titre} — ${minutes} min</h3>
        <p><strong>Activités de l’enseignant :</strong> ${p.activite}</p>
        <p><strong>Activités des apprenants :</strong> ${p.apprenant}</p>
        <p><strong>Consigne :</strong> ${afficher(donnees.consigne, "Consigne à préciser selon la situation d’apprentissage.")}</p>
        <p><strong>Résultats / traces attendus :</strong> ${p.trace}</p>
      </div>`;
  }).join("");

  const html = `
    <div class="info">
      <div><strong>Classe :</strong> ${afficher(classe)}</div>
      <div><strong>Discipline :</strong> ${afficher(discipline)}</div>
      <div><strong>Leçon :</strong> ${afficher(notion)}</div>
      <div><strong>Durée :</strong> ${afficher(duree)} minutes</div>
      <div><strong>Semaine / période :</strong> ${afficher(donnees.semaine)}</div>
      <div><strong>Effectif :</strong> ${afficher(donnees.effectif)}</div>
      <div><strong>Enseignant :</strong> ${afficher(donnees.enseignant)}</div>
    </div>

    <h3>I. Compétence visée</h3>
    <p>${afficher(donnees.competence, "À préciser selon le programme officiel.")}</p>

    <h3>II. Objectif d’apprentissage</h3>
    <p>${afficher(donnees.objectif, "À préciser en fonction de la notion étudiée.")}</p>

    <h3>III. Résultats attendus</h3>
    <p>${afficher(donnees.resultats, "L’apprenant réalise correctement la tâche liée à la notion étudiée.")}</p>

    <h3>IV. Prérequis</h3>
    <p>${afficher(donnees.prerequis)}</p>

    <h3>V. Matériel et supports</h3>
    <p>${afficher(donnees.materiel)}</p>

    <h3>VI. Déroulement de la séance</h3>
    <table>
      <thead>
        <tr>
          <th>Phase</th>
          <th>Rôle de l’enseignant</th>
          <th>Activité des apprenants</th>
        </tr>
      </thead>
      <tbody>
        ${phases.map(function(p) {
          return `<tr>
            <td>${p.titre}</td>
            <td>${p.activite}</td>
            <td>${p.apprenant}</td>
          </tr>`;
        }).join("")}
      </tbody>
    </table>

    ${phasesHTML}

    <h3>VII. Évaluation de la séance</h3>
    <p><strong>Exercice / questions :</strong> ${afficher(donnees.evaluation, "Prévoir des questions ou une tâche individuelle en rapport direct avec l’objectif.")}</p>

    <h3>VIII. Remédiation et prolongement</h3>
    <p>Reprendre la notion avec des exemples plus simples pour les apprenants en difficulté. Proposer une activité de réinvestissement aux apprenants ayant atteint l’objectif.</p>

    <h3>IX. Bilan de l’enseignant</h3>
    <p>Objectif atteint : ☐ Oui ☐ Partiellement ☐ Non</p>
    <p>Difficultés observées : ................................................................................</p>
    <p>Décisions pour la prochaine séance : ...............................................................</p>

    <p><em>Note : cette fiche constitue une trame de préparation. Vérifier et adapter les phases, les consignes, les contenus et les critères d’évaluation au guide pédagogique officiel de la classe et de la discipline.</em></p>
  `;

  document.getElementById("contenuFiche").innerHTML = html;
  document.getElementById("fiche").style.display = "block";
  document.getElementById("fiche").scrollIntoView({ behavior: "smooth" });
}

function modifierFiche() {
  document.getElementById("formulaire").scrollIntoView({ behavior: "smooth" });
}

function reinitialiser() {
  if (!confirm("Effacer tous les champs du formulaire ?")) return;

  document.querySelectorAll("#formulaire input, #formulaire textarea").forEach(function(el) {
    el.value = "";
  });

  document.getElementById("classe").value = "CE1";
  document.getElementById("discipline").value = "Français";
  document.getElementById("duree").value = "30";
  document.getElementById("fiche").style.display = "none";
  document.getElementById("contenuFiche").innerHTML = "";
}
</script>
</body>
</html>
