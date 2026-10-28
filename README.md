
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
  --fond: #f4f7f4;
  --texte: #203328;
  --bordure: #cbd8ce;
}
* { box-sizing: border-box; }
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: var(--fond);
  color: var(--texte);
  line-height: 1.5;
}
header {
  background: var(--vert);
  color: white;
  padding: 22px 14px;
  text-align: center;
}
header h1 { margin: 0 0 8px; font-size: 25px; }
header p { margin: 0; }
main {
  width: min(100% - 24px, 950px);
  margin: 20px auto;
}
.panel {
  background: white;
  border: 1px solid var(--bordure);
  border-radius: 12px;
  padding: 18px;
  margin-bottom: 18px;
}
h2 { color: var(--vert); margin-top: 0; }
label {
  display: block;
  font-weight: bold;
  margin: 13px 0 5px;
}
input, select, textarea {
  width: 100%;
  padding: 11px;
  border: 1px solid #9cad9f;
  border-radius: 7px;
  background: white;
  font: inherit;
}
textarea { min-height: 90px; resize: vertical; }
button {
  border: 0;
  border-radius: 7px;
  padding: 12px 15px;
  margin: 8px 5px 0 0;
  background: var(--vert);
  color: white;
  font-weight: bold;
  font-size: 15px;
  cursor: pointer;
}
button.secondary { background: #46564b; }
button.light {
  background: var(--vert-clair);
  color: var(--vert);
  border: 1px solid var(--bordure);
}
.note {
  padding: 12px;
  border-left: 4px solid var(--vert);
  background: var(--vert-clair);
  border-radius: 5px;
}
#resultat { display: none; }
.document {
  background: white;
  padding: 20px;
  border: 1px solid var(--bordure);
  border-radius: 8px;
  margin-top: 15px;
}
.document h2, .document h3 { text-align: center; }
table {
  width: 100%;
  border-collapse: collapse;
  margin: 12px 0;
}
th, td {
  border: 1px solid #829286;
  padding: 8px;
  text-align: left;
  vertical-align: top;
}
th { background: var(--vert-clair); }
.small { font-size: 13px; color: #536358; }
footer {
  text-align: center;
  padding: 20px;
  font-size: 13px;
}
@media print {
  body { background: white; }
  header, #formulaire, #programme, .actions, footer {
    display: none !important;
  }
  main { width: 100%; margin: 0; }
  .panel { border: none; padding: 0; }
  .document { border: none; padding: 0; }
  #resultat { display: block !important; }
  .document { page-break-after: always; }
  button { display: none; }
}
</style>
</head>
<body>

<header>
  <h1>Bot pédagogique APC Bénin</h1>
  <p>Préparation des leçons et résumés de cours au primaire</p>
</header>

<main>
  <section class="panel" id="formulaire">
    <h2>1. Préparer une leçon</h2>
    <p class="note">
      Sélectionne la classe, la discipline et la notion.
      Complète les informations pour produire une fiche de travail.
    </p>

    <label for="classe">Classe</label>
    <select id="classe">
      <option value="CI">CI</option>
      <option value="CP">CP</option>
      <option value="CE1" selected>CE1</option>
      <option value="CE2">CE2</option>
      <option value="CM1">CM1</option>
      <option value="CM2">CM2</option>
    </select>

    <label for="discipline">Discipline</label>
    <select id="discipline">
      <option>Français</option>
      <option>Mathématiques - Arithmétique</option>
      <option>Mathématiques - Géométrie</option>
      <option>Mathématiques - Mesures</option>
      <option>ES - Morale</option>
      <option>ES - Civisme</option>
      <option>ES - Compétence 2 : Histoire et Géographie</option>
      <option>ES - Compétence 3 : Langues et culture</option>
      <option>EST</option>
      <option>EA - Dessin</option>
      <option>EA - Chant</option>
      <option>EA - Travaux manuels</option>
      <option>EA - Poésie</option>
      <option>EA - Conte</option>
      <option>EA - Couture</option>
      <option>EPS</option>
    </select>

    <label for="documentType">Document à générer</label>
    <select id="documentType">
      <option value="lesdeux">Fiche de préparation et résumé</option>
      <option value="fiche">Fiche de préparation seulement</option>
      <option value="resume">Résumé de cours seulement</option>
    </select>

    <label for="notion">Notion ou titre de la leçon</label>
    <input id="notion" list="notions" placeholder="Ex. : Les diphtongues" required>
    <datalist id="notions">
      <option value="Les diphtongues et doubles consonnes">
      <option value="Lecture d'un texte">
      <option value="Compréhension d'un texte narratif">
      <option value="Expression écrite">
      <option value="Vocabulaire">
      <option value="Le nom">
      <option value="Le déterminant">
      <option value="Le sujet et le verbe">
      <option value="La conjugaison">
      <option value="L'orthographe">
      <option value="La phrase">
      <option value="Les nombres">
      <option value="Les opérations">
      <option value="Les figures géométriques">
      <option value="Les mesures">
    </datalist>

    <label for="duree">Durée en minutes</label>
    <input id="duree" type="number" min="5" value="45">

    <label for="semaine">Semaine ou période</label>
    <input id="semaine" placeholder="Ex. : Semaine 1">

    <label for="objectif">Objectif d'apprentissage</label>
    <textarea id="objectif" placeholder="Ce que l'élève devra savoir ou savoir faire."></textarea>

    <label for="materiel">Matériel didactique</label>
    <textarea id="materiel" placeholder="Objets réels, tableau, ardoises, manuel, images..."></textarea>

    <label for="prerequis">Prérequis</label>
    <textarea id="prerequis" placeholder="Connaissances nécessaires avant la leçon."></textarea>

    <button onclick="generer()">Générer le document</button>
    <button class="secondary" onclick="reinitialiser()">Effacer les champs</button>
  </section>

  <section class="panel" id="programme">
    <h2>2. Programme des diphtongues et doubles consonnes — CE1</h2>
    <p class="small">
      Programme transcrit à partir des informations communiquées.
      Certains éléments doivent encore être vérifiés sur le document original.
    </p>

    <label for="semaineLecture">Choisir une semaine</label>
    <select id="semaineLecture" onchange="afficherProgramme()">
      <option value="0">Semaine 1</option>
      <option value="1">Semaine 2</option>
      <option value="2">Semaine 3</option>
      <option value="3">Semaine 4</option>
    </select>
    <div id="contenuProgramme"></div>
    <button class="light" onclick="utiliserProgramme()">Utiliser comme notion de leçon</button>
  </section>

  <section class="panel" id="resultat">
    <h2>3. Documents générés</h2>
    <div class="actions">
      <button onclick="window.print()">Imprimer / Enregistrer en PDF</button>
      <button class="secondary" onclick="copierDocument()">Copier le texte</button>
    </div>
    <div id="documents"></div>
  </section>
</main>

<footer>
  Bot pédagogique APC Bénin — outil de préparation pédagogique.
  Vérifier les contenus avec les programmes, guides et manuels officiels.
</footer>

<script>
const programmeLecture = [
  [
    "AM, EM, AN, EN",
    "ON, OM",
    "OIN",
    "IEN, ION",
    "AU, EAU, ONT, OS",
    "OI, VOIX, LIT",
    "IN, IL, AIN, EIN",
    "EU, ŒU"
  ],
  [
    "OR, PAR",
    "ET = É, EZ = É, AI = É",
    "AY, OU, UY",
    "AI, EI, AIS, AIT",
    "AIL, AILLE",
    "ILL, EUIL, FEUILLE",
    "EIL, ELLE",
    "OU, OUILLE"
  ],
  [
    "ŒUR, EUR, EURE",
    "OIR, LIRE",
    "G = J",
    "G = GU",
    "GN",
    "QU = K = C",
    "C = S ; Ç = S",
    "S = Z"
  ],
  [
    "IEZ, IER, IED",
    "CH, TCH",
    "PH = F, TH = T",
    "AC, OC, IC, EC",
    "TION = SION",
    "BL, PL, VL, GL, FL, CL…",
    "BR, TR, CR, PR, DE, FR…",
    "DJ, GB, KP"
  ]
];

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

function afficherProgramme() {
  const semaine = Number(document.getElementById("semaineLecture").value);
  const liste = programmeLecture[semaine];

  let html = "<table><thead><tr><th>Jour de progression</th><th>Contenu transcrit</th></tr></thead><tbody>";
  liste.forEach(function(item, index) {
    html += "<tr><td>Étude " + (index + 1) + "</td><td>" + echapper(item) + "</td></tr>";
  });
  html += "</tbody></table>";
  html += '<p class="small">Attention : vérifier les graphies et les exemples incertains avant de construire les exercices.</p>';

  document.getElementById("contenuProgramme").innerHTML = html;
}

function utiliserProgramme() {
  const semaine = Number(document.getElementById("semaineLecture").value);
  document.getElementById("classe").value = "CE1";
  document.getElementById("discipline").value = "Français";
  document.getElementById("notion").value =
    "Diphtongues et doubles consonnes — semaine " + (semaine + 1);
  document.getElementById("semaine").value = "Semaine " + (semaine + 1);
  document.getElementById("objectif").value =
    "Amener les élèves à reconnaître, lire et utiliser les graphies étudiées dans des syllabes, des mots et des phrases.";
  document.getElementById("materiel").value =
    "Tableau, ardoises, cahiers, cartes de graphies, mots et texte de lecture adaptés.";
  document.getElementById("formulaire").scrollIntoView({behavior:"smooth"});
}

function generer() {
  const classe = document.getElementById("classe").value;
  const discipline = document.getElementById("discipline").value;
  const type = document.getElementById("documentType").value;
  const notion = document.getElementById("notion").value.trim();
  const duree = Number(document.getElementById("duree").value) || 45;
  const semaine = document.getElementById("semaine").value.trim() || "À préciser";
  const objectif = document.getElementById("objectif").value.trim() ||
    "À préciser par l'enseignant selon le programme et le guide pédagogique.";
  const materiel = document.getElementById("materiel").value.trim() ||
    "Tableau, ardoises, cahiers et matériel adapté à la leçon.";
  const prerequis = document.getElementById("prerequis").value.trim() ||
    "À déterminer selon les acquis des élèves.";

  if (!notion) {
    alert("Saisis d'abord la notion de la leçon.");
    document.getElementById("notion").focus();
    return;
  }

  let html = "";

  if (type === "fiche" || type === "lesdeux") {
    html += `
      <article class="document">
        <h2>FICHE DE PRÉPARATION</h2>
        <p><strong>République du Bénin — Enseignement primaire</strong></p>
        <table>
          <tr><th>Classe</th><td>${echapper(classe)}</td>
          <th>Discipline</th><td>${echapper(discipline)}</td></tr>
          <tr><th>Notion</th><td colspan="3">${echapper(notion)}</td></tr>
          <tr><th>Durée</th><td>${duree} minutes</td>
          <th>Période</th><td>${echapper(semaine)}</td></tr>
          <tr><th>Objectif</th><td colspan="3">${echapper(objectif)}</td></tr>
          <tr><th>Prérequis</th><td colspan="3">${echapper(prerequis)}</td></tr>
          <tr><th>Matériel</th><td colspan="3">${echapper(materiel)}</td></tr>
        </table>

        <h3>Déroulement pédagogique proposé</h3>
        <table>
          <thead>
            <tr>
              <th>Phase</th><th>Activités de l'enseignant</th>
              <th>Activités des élèves</th><th>Résultats attendus / vérification</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>1. Mise en situation</td>
              <td>Présente une situation concrète, un objet, une question ou un support en lien avec la notion.</td>
              <td>Observent, écoutent, répondent et expriment leurs idées.</td>
              <td>Les élèves identifient le problème ou la tâche à réaliser.</td>
            </tr>
            <tr>
              <td>2. Recherche / exploration</td>
              <td>Donne une consigne claire, organise les recherches et apporte une aide adaptée sans faire le travail à la place des élèves.</td>
              <td>Recherchent individuellement ou en groupe, manipulent, lisent ou proposent des réponses.</td>
              <td>Les élèves produisent des propositions en rapport avec la notion.</td>
            </tr>
            <tr>
              <td>3. Mise en commun</td>
              <td>Invite les élèves à présenter leurs résultats et fait comparer les démarches.</td>
              <td>Présentent, expliquent, écoutent et confrontent leurs réponses.</td>
              <td>Les propositions sont expliquées et discutées.</td>
            </tr>
            <tr>
              <td>4. Structuration</td>
              <td>Guide la correction, fait ressortir les éléments essentiels et formule la règle ou la synthèse avec la classe.</td>
              <td>Corrigent, reformulent et notent la synthèse dans le cahier si nécessaire.</td>
              <td>Les élèves formulent ou retiennent l'essentiel de la leçon.</td>
            </tr>
            <tr>
              <td>5. Application</td>
              <td>Propose des exercices progressifs et accompagne les élèves qui en ont besoin.</td>
              <td>Résolvent les exercices et expliquent leurs réponses.</td>
              <td>Les élèves appliquent la notion à des tâches nouvelles.</td>
            </tr>
            <tr>
              <td>6. Évaluation</td>
              <td>Donne une consigne individuelle permettant de vérifier l'objectif.</td>
              <td>Réalisent le travail demandé individuellement.</td>
              <td>Les réponses permettent de repérer les acquis et les difficultés.</td>
            </tr>
            <tr>
              <td>7. Remédiation / prolongement</td>
              <td>Prévoit un exercice de reprise pour les difficultés observées et une activité supplémentaire pour les élèves prêts.</td>
              <td>Reprennent les éléments non maîtrisés ou réalisent une activité complémentaire.</td>
              <td>Les difficultés sont ciblées et les apprentissages consolidés.</td>
            </tr>
          </tbody>
        </table>
        <p><strong>Consigne principale :</strong> À adapter précisément à la notion et au niveau des élèves.</p>
        <p><strong>Critère d'évaluation :</strong> L'élève réalise correctement la tâche correspondant à l'objectif annoncé.</p>
        <p class="small">Modèle de travail à adapter au canevas officiel de l'école et au guide pédagogique applicable.</p>
      </article>`;
  }

  if (type === "resume" || type === "lesdeux") {
    html += `
      <article class="document">
        <h2>RÉSUMÉ DE COURS</h2>
        <p><strong>Classe :</strong> ${echapper(classe)}</p>
        <p><strong>Discipline :</strong> ${echapper(discipline)}</p>
        <p><strong>Leçon :</strong> ${echapper(notion)}</p>
        <h3>Ce qu'il faut retenir</h3>
        <p>${echapper(objectif)}</p>
        <p><strong>Notion étudiée :</strong> ${echapper(notion)}.</p>
        <p>
          Le contenu précis de la leçon doit être complété à partir du programme,
          du guide pédagogique et du manuel correspondant à la classe.
          Ce résumé automatique est une trame de rédaction et non un cours officiel complet.
        </p>
        <h3>Exemples</h3>
        <p>Ajouter ici des exemples simples, adaptés au niveau des élèves et vérifiés par l'enseignant.</p>
        <h3>Application</h3>
        <p>1. Explique la notion étudiée avec tes propres mots.</p>
        <p>2. Donne deux exemples correspondant à la leçon.</p>
        <p>3. Réalise un exercice proposé par l'enseignant.</p>
      </article>`;
  }

  document.getElementById("documents").innerHTML = html;
  document.getElementById("resultat").style.display = "block";
  document.getElementById("resultat").scrollIntoView({behavior:"smooth"});
}

function copierDocument() {
  const texte = document.getElementById("documents").innerText;
  if (!texte.trim()) {
    alert("Génère d'abord un document.");
    return;
  }

  if (navigator.clipboard && navigator.clipboard.writeText) {
    navigator.clipboard.writeText(texte)
      .then(() => alert("Texte copié."))
      .catch(() => copierAncienMode(texte));
  } else {
    copierAncienMode(texte);
  }
}

function copierAncienMode(texte) {
  const zone = document.createElement("textarea");
  zone.value = texte;
  document.body.appendChild(zone);
  zone.select();
  try {
    document.execCommand("copy");
    alert("Texte copié si ton navigateur a autorisé la copie.");
  } catch (e) {
    alert("Copie automatique impossible. Sélectionne le texte du document.");
  }
  zone.remove();
}

function reinitialiser() {
  document.getElementById("notion").value = "";
  document.getElementById("semaine").value = "";
  document.getElementById("objectif").value = "";
  document.getElementById("materiel").value = "";
  document.getElementById("prerequis").value = "";
  document.getElementById("resultat").style.display = "none";
  document.getElementById("documents").innerHTML = "";
}

afficherProgramme();
</script>
</body>
</html>
