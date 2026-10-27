index.html.

<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Bot pédagogique APC Bénin</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #f0f5f1;
      color: #183323;
    }
    header {
      background: #176534;
      color: white;
      text-align: center;
      padding: 22px 12px;
    }
    main {
      max-width: 800px;
      margin: 20px auto;
      padding: 16px;
    }
    section {
      background: white;
      padding: 20px;
      border-radius: 12px;
    }
    label {
      display: block;
      margin-top: 14px;
      font-weight: bold;
    }
    input, select, textarea {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      box-sizing: border-box;
      border: 1px solid #aaa;
      border-radius: 6px;
    }
    button {
      margin-top: 18px;
      padding: 12px;
      background: #176534;
      color: white;
      border: 0;
      border-radius: 6px;
      font-size: 16px;
    }
    #resultat {
      display: none;
      margin-top: 20px;
      padding: 15px;
      border: 1px solid #176534;
      background: white;
    }
    @media print {
      header, section, button {
        display: none;
      }
      #resultat {
        display: block;
        border: none;
      }
    }
  </style>
</head>
<body>
  <header>
    <h1>Bot pédagogique APC Bénin</h1>
    <p>Préparation des fiches pédagogiques du primaire</p>
  </header>

  <main>
    <section>
      <h2>Préparer une séance</h2>

      <label for="classe">Classe</label>
      <select id="classe">
        <option>CI</option>
        <option>CP</option>
        <option>CE1</option>
        <option>CE2</option>
        <option>CM1</option>
        <option>CM2</option>
      </select>

      <label for="discipline">Discipline</label>
      <select id="discipline">
        <option>Français</option>
        <option>Mathématiques</option>
        <option>Éducation sociale</option>
        <option>EST</option>
        <option>Éducation artistique</option>
        <option>EPS</option>
      </select>

      <label for="titre">Titre de la leçon</label>
      <input id="titre" placeholder="Ex. : Les diphtongues">

      <label for="duree">Durée</label>
      <input id="duree" placeholder="Ex. : 30 minutes">

      <label for="objectif">Objectif spécifique</label>
      <textarea id="objectif" placeholder="Ce que l'élève doit apprendre"></textarea>

      <button type="button" onclick="generer()">Générer la fiche</button>
      <button type="button" onclick="window.print()">Imprimer / PDF</button>
    </section>

    <div id="resultat"></div>
  </main>

  <script>
    function generer() {
      const titre = document.getElementById("titre").value.trim();

      if (!titre) {
        alert("Veuillez saisir le titre de la leçon.");
        return;
      }

      const classe = document.getElementById("classe").value;
      const discipline = document.getElementById("discipline").value;
      const duree = document.getElementById("duree").value || "À préciser";
      const objectif = document.getElementById("objectif").value || "À compléter";

      const resultat = document.getElementById("resultat");
      resultat.innerHTML = `
        <h1>FICHE DE PRÉPARATION APC</h1>
        <p><b>Classe :</b> ${classe}</p>
        <p><b>Discipline :</b> ${discipline}</p>
        <p><b>Leçon :</b> ${titre}</p>
        <p><b>Durée :</b> ${duree}</p>
        <h2>Objectif spécifique</h2>
        <p>${objectif}</p>
        <h2>Déroulement</h2>
        <p><b>Découverte :</b> Présentation de la situation d'apprentissage.</p>
        <p><b>Recherche :</b> Les élèves cherchent une solution.</p>
        <p><b>Mise en commun :</b> Comparaison des réponses.</p>
        <p><b>Structuration :</b> Résumé de la notion étudiée.</p>
        <p><b>Évaluation :</b> Exercice individuel de vérification.</p>
      `;
      resultat.style.display = "block";
      resultat.scrollIntoView({behavior: "smooth"});
    }
  </script>
</body>
</html>
