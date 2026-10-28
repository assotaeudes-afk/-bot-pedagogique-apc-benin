index.html
<script>
const $ = id => document.getElementById(id);
const valeur = id => $(id).value.trim();

const echapper = texte => String(texte || "").replace(/[&<>"']/g, c => ({
  "&":"&amp;", "<":"&lt;", ">":"&gt;", '"':"&quot;", "'":"&#39;"
}[c]));

const afficher = texte => echapper(texte).replace(/\n/g, "<br>");

function bloc(titre, texte) {
  if (!texte) return "";
  return `<section class="content-block">
    <h3>${echapper(titre)}</h3><div>${afficher(texte)}</div>
  </section>`;
}

function cellule(titre, texte) {
  return `<div><strong>${echapper(titre)}</strong>${afficher(texte || "Non renseigné")}</div>`;
}

/* Repères pédagogiques indicatifs par discipline.
   Ils servent de propositions à adapter par l'enseignant. */
const profils = {
  "Français": {
    decouverte: "Présenter des mots, phrases, textes ou supports liés à la notion. Demander aux apprenants d'observer, de lire ou d'écouter.",
    apprenants: "Observer les supports, lire ou écouter, relever les éléments utiles et formuler des hypothèses.",
    construction: "Faire comparer les réponses, guider la formulation de la règle ou de la notion, puis faire produire une trace écrite.",
    application: "Proposer des exercices oraux et écrits progressifs, puis une tâche de réinvestissement.",
    evaluation: "Vérifier que les apprenants reconnaissent la notion et savent l'utiliser dans un exemple nouveau.",
    resultat: "Les apprenants identifient la notion étudiée, expliquent leur démarche et réalisent correctement les exercices."
  },
  "Mathématiques": {
    decouverte: "Présenter une situation-problème, du matériel concret, des figures, des nombres ou des mesures adaptés à la notion.",
    apprenants: "Manipuler, observer, compter, mesurer, tracer, calculer ou rechercher une solution individuellement ou en groupe.",
    construction: "Faire expliquer les démarches, comparer les stratégies et institutionnaliser la règle, la propriété ou la technique.",
    application: "Proposer des exercices gradués et un problème de transfert dans une situation concrète.",
    evaluation: "Donner un exercice ou un problème permettant de vérifier la procédure et la justesse du résultat.",
    resultat: "Les apprenants choisissent une démarche pertinente, justifient leur réponse et obtiennent un résultat vérifiable."
  },
  "Éducation sociale": {
    decouverte: "Présenter une situation de vie, une image, un récit, un document ou un problème social en lien avec la leçon.",
    apprenants: "Observer, décrire, raconter, comparer les situations et exprimer leurs idées en respectant les autres.",
    construction: "Guider les échanges, clarifier les faits et faire dégager les valeurs, règles ou connaissances essentielles.",
    application: "Proposer une étude de cas, un jeu de rôle, un classement ou une action adaptée au thème.",
    evaluation: "Poser des questions de compréhension et proposer une situation où l'apprenant doit appliquer ce qu'il a appris.",
    resultat: "Les apprenants expliquent les notions essentielles et proposent une conduite ou une solution adaptée à la situation."
  },
  "EST": {
    decouverte: "Présenter un objet, un phénomène, un outil, une image ou une situation d'observation en lien avec la leçon.",
    apprenants: "Observer, décrire, questionner, manipuler avec prudence et relever les informations utiles.",
    construction: "Aider à comparer les observations, expliquer le phénomène ou la technique et établir les étapes essentielles.",
    application: "Faire réaliser une expérience simple, une démonstration, un montage ou une tâche pratique adaptée.",
    evaluation: "Vérifier la compréhension, le respect des étapes, la sécurité et la qualité de la réalisation.",
    resultat: "Les apprenants décrivent le phénomène ou réalisent la tâche demandée en respectant les consignes de sécurité."
  },
  "Éducation artistique": {
    decouverte: "Présenter un modèle, une œuvre, un rythme, un chant, un texte ou le matériel nécessaire à la production.",
    apprenants: "Écouter, observer, répéter, expérimenter les gestes ou les techniques et exprimer leurs impressions.",
    construction: "Démontrer les gestes ou techniques, guider les essais et faire repérer les critères d'une réalisation réussie.",
    application: "Faire répéter, interpréter, dessiner, fabriquer ou réaliser une production selon la discipline choisie.",
    evaluation: "Observer la participation, la maîtrise de la technique, le respect des consignes et la production obtenue.",
    resultat: "Les apprenants participent activement et présentent une réalisation ou une interprétation correspondant aux critères annoncés."
  },
  "EPS": {
    decouverte: "Présenter l'objectif moteur, aménager l'espace et expliquer les règles et les consignes de sécurité.",
    apprenants: "Écouter, observer la démonstration, s'échauffer puis essayer les mouvements ou situations proposés.",
    construction: "Démontrer le geste, décomposer les étapes et corriger les mouvements avec des conseils adaptés.",
    application: "Organiser des ateliers, des répétitions ou des jeux adaptés au niveau des apprenants.",
    evaluation: "Observer l'exécution du geste, le respect des règles, la progression et la sécurité.",
    resultat: "Les apprenants réalisent le mouvement ou la tâche motrice visée en respectant les règles et les consignes."
  }
};

function profilActuel() {
  const d = valeur("discipline");
  if (d.includes("Éducation sociale")) return profils["Éducation sociale"];
  if (d.includes("Éducation artistique")) return profils["Éducation artistique"];
  if (d === "EPS") return profils["EPS"];
  if (d === "EST") return profils["EST"];
  if (d === "Mathématiques") return profils["Mathématiques"];
  return profils["Français"];
}

function activiteEnseignant(phase, saisie, p) {
  if (saisie) return saisie;
  const suggestions = {
    "Motivation et préparation":
      "Présenter une situation d'entrée en lien avec la notion et annoncer la tâche à réaliser.",
    "Mise en situation et acquis antérieurs":
      "Poser des questions de rappel, présenter la situation-problème et recueillir les réponses.",
    "Découverte et recherche": p.decouverte,
    "Construction et structuration": p.construction,
    "Application et entraînement": p.application,
    "Évaluation": p.evaluation,
    "Objectivation et projection":
      "Demander aux apprenants ce qu'ils ont retenu, relever les difficultés et annoncer la suite."
  };
  return suggestions[phase] || "Donner une consigne claire et observer les démarches des apprenants.";
}

function activiteApprenant(phase, p) {
  const activites = {
    "Motivation et préparation":
      "Écouter, observer et se préparer à participer.",
    "Mise en situation et acquis antérieurs":
      "Rappeler les acquis, répondre aux questions et comprendre le problème posé.",
    "Découverte et recherche": p.apprenants,
    "Construction et structuration":
      "Expliquer les démarches, comparer les réponses et retenir l'essentiel.",
    "Application et entraînement":
      "Réaliser les exercices, appliquer la notion et corriger les erreurs.",
    "Évaluation":
      "Répondre individuellement aux questions et produire le travail demandé.",
    "Objectivation et projection":
      "Dire ce qui a été appris et identifier ce qui reste à améliorer."
  };
  return activites[phase] || "Participer à la tâche et présenter sa production.";
}

function resultatAttendu(phase, saisie, p) {
  if (saisie) return saisie;
  const resultats = {
    "Motivation et préparation":
      "Les apprenants sont attentifs et comprennent la situation proposée.",
    "Mise en situation et acquis antérieurs":
      "Les acquis utiles sont rappelés et le problème à résoudre est compris.",
    "Découverte et recherche": p.resultat,
    "Construction et structuration":
      "Les apprenants formulent ou retiennent les savoirs essentiels de la leçon.",
    "Application et entraînement":
      "Les apprenants appliquent la notion à des tâches adaptées à leur niveau.",
    "Évaluation": p.resultat,
    "Objectivation et projection":
      "Les apprenants expriment l'essentiel retenu et identifient la prochaine étape."
  };
  return resultats[phase] || "Les apprenants réalisent la tâche demandée.";
}

$("form").addEventListener("submit", function(e) {
  e.preventDefault();

  const total = Number(valeur("duree"));
  if (!valeur("titre")) {
    alert("Saisis le titre de la leçon.");
    $("titre").focus();
    return;
  }
  if (!total || total < 5) {
    alert("Indique une durée totale d'au moins 5 minutes.");
    $("duree").focus();
    return;
  }

  const p = profilActuel();
  const etapes = [
    ["PHASES PRÉLIMINAIRES", "Motivation et préparation", "motivation", 10],
    ["INTRODUCTION", "Mise en situation et acquis antérieurs", "intro", 15],
    ["RÉALISATION", "Découverte et recherche", "decouverte", 20],
    ["RÉALISATION", "Construction et structuration", "construction", 20],
    ["RÉALISATION", "Application et entraînement", "application", 15],
    ["RETOUR ET PROJECTION", "Évaluation", "evaluation", 15],
    ["RETOUR ET PROJECTION", "Objectivation et projection", "projection", 5]
  ];

  let durees = etapes.map(e => Math.floor(total * e[3] / 100));
  let reste = total - durees.reduce((a,b) => a+b, 0);
  for (let i = 0; i < reste; i++) durees[i % durees.length]++;

  // Garantir au moins une minute par étape, même pour une séance courte.
  if (total >= etapes.length) {
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

  let tableau = "";
  let sectionActuelle = "";

  etapes.forEach((etape, i) => {
    const [section, phase, id] = etape;
    if (section !== sectionActuelle) {
      sectionActuelle = section;
      tableau += `<tr class="phase-title"><td colspan="5">${echapper(section)}</td></tr>`;
    }

    const consigne = activiteEnseignant(phase, valeur(id), p);
    const activites = activiteApprenant(phase, p);
    const resultats = resultatAttendu(
      phase,
      phase === "Évaluation" ? valeur("resultats") : "",
      p
    );

    tableau += `<tr>
      <td>${echapper(phase)}<br><strong>${durees[i]} min</strong></td>
      <td>${afficher(consigne)}</td>
      <td>${afficher(activites)}</td>
      <td>${afficher(resultats)}</td>
      <td>${phase === "Évaluation"
        ? afficher(valeur("evaluation") || p.evaluation)
        : "Observation des démarches et des productions."}</td>
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

    <h3 style="text-align:center;margin-top:22px">DÉROULEMENT DE LA SÉANCE</h3>
    <table>
      <thead><tr>
        <th style="width:17%">PHASE / DURÉE</th>
        <th style="width:23%">CONSIGNES ET ACTIVITÉS DE L'ENSEIGNANT</th>
        <th style="width:23%">ACTIVITÉS DES APPRENANTS</th>
        <th style="width:19%">RÉSULTATS ATTENDUS</th>
        <th style="width:18%">ÉVALUATION / OBSERVATION</th>
      </tr></thead>
      <tbody>${tableau}</tbody>
    </table>

    ${bloc("REMÉDIATION", valeur("remediation"))}
    ${bloc("NOTES PERSONNELLES DE L'ENSEIGNANT(E)", valeur("notes"))}
    <p class="small-note">Les propositions automatiques sont indicatives. Adapter les contenus, les étapes, les durées et les critères au programme, à la discipline, au niveau de la classe et aux documents pédagogiques de référence.</p>
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