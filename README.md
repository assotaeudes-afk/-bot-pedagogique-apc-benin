HTML

<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Bot pédagogique APC Bénin</title>
<style>
:root{--vert:#176534;--clair:#f0f5f1;--bord:#cbd8ce}
*{box-sizing:border-box}
body{margin:0;background:var(--clair);color:#183323;font-family:Arial,sans-serif;line-height:1.5}
header{background:var(--vert);color:white;padding:20px 12px;text-align:center}
header h1{font-size:24px;margin:0 0 6px}
main{max-width:950px;margin:18px auto;padding:0 12px}
.panel{background:white;padding:18px;border-radius:10px;margin-bottom:16px;border:1px solid var(--bord)}
h2{color:var(--vert);font-size:21px;margin-top:0}
h3{color:var(--vert);font-size:17px}
.grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:12px}
label{font-weight:bold;display:block;margin-bottom:5px}
input,select,textarea{width:100%;padding:10px;border:1px solid #9cad9f;border-radius:6px;font:inherit;background:white;color:#183323}
textarea{min-height:75px;resize:vertical}
.full{grid-column:1/-1}
.actions{display:flex;flex-wrap:wrap;gap:10px;margin-top:15px}
button{padding:12px 15px;border:0;border-radius:6px;background:var(--vert);color:white;font-weight:bold;font-size:15px;cursor:pointer}
button.secondary{background:#42574a}
button.light{background:#e5eee7;color:#183323}
#fiche{display:none;background:white}
#fiche h2{text-align:center}
.meta{width:100%;border-collapse:collapse;margin:12px 0}
.meta td,.meta th,.phases td,.phases th{border:1px solid #8d9d91;padding:7px;vertical-align:top;text-align:left;overflow-wrap:anywhere}
.meta td:first-child{font-weight:bold;width:28%}
.phases{width:100%;border-collapse:collapse;table-layout:fixed;font-size:12px}
.phases th{background:#e5eee7}
.phases th:nth-child(1){width:13%}
.phases th:nth-child(2){width:10%}
.phases th:nth-child(3){width:28%}
.phases th:nth-child(4){width:25%}
.phases th:nth-child(5){width:24%}
.info{margin:10px 0;white-space:pre-wrap;overflow-wrap:anywhere}
.section-title{font-weight:bold;color:var(--vert);margin-top:14px}
footer{text-align:center;font-size:12px;padding:18px;color:#42574a}
@media(max-width:600px){
 .grid{grid-template-columns:1fr}
 .full{grid-column:auto}
 .panel{padding:13px}
 .phases{font-size:10px}
 .phases td,.phases th{padding:4px}
}
@media print{
 @page{size:A4;margin:12mm}
 body{background:white;color:#000;font-size:11pt}
 header,.form-panel,.actions,footer{display:none!important}
 main{max-width:none;margin:0;padding:0}
 .panel{border:0;padding:0;margin:0}
 #fiche{display:block!important}
 #fiche h2{font-size:16pt;color:#000}
 h3,.section-title{color:#000}
 .phases{font-size:8pt}
 .phases th{background:#eee!important}
 tr{break-inside:avoid}
}
</style>
</head>
<body>
<header>
<h1>Bot pédagogique APC Bénin</h1>
<p>Préparation de fiches pédagogiques — CI, CP, CE1, CE2, CM1 et CM2</p>
</header>

<main>
<section class="panel form-panel">
<h2>Préparer une séance</h2>
<p>Renseigne les informations puis appuie sur « Générer la fiche ».</p>

<form id="formulaire">
<div class="grid">
<div>
<label for="ecole">École</label>
<input id="ecole" placeholder="Nom de l'école">
</div>
<div>
<label for="enseignant">Enseignant(e)</label>
<input id="enseignant" placeholder="Nom de l'enseignant(e)">
</div>
<div>
<label for="date">Date</label>
<input id="date" type="date">
</div>
<div>
<label for="periode">Période / trimestre</label>
<input id="periode" placeholder="Ex. : 1er trimestre">
</div>
<div>
<label for="classe">Classe *</label>
<select id="classe" required>
<option value="">Choisir</option>
<option>CI</option><option>CP</option><option>CE1</option>
<option>CE2</option><option>CM1</option><option>CM2</option>
</select>
</div>
<div>
<label for="discipline">Discipline *</label>
<select id="discipline" required>
<option value="">Choisir</option>
<option>Français</option><option>Mathématiques</option>
<option>Éducation sociale — Morale</option>
<option>Éducation sociale — Civisme</option>
<option>Éducation sociale — Histoire</option>
<option>Éducation sociale — Géographie</option>
<option>Éducation sociale — Langues et culture</option>
<option>EST</option><option>Éducation artistique — Dessin</option>
<option>Éducation artistique — Chant</option>
<option>Éducation artistique — Travaux manuels</option>
<option>Éducation artistique — Poésie</option>
<option>Éducation artistique — Conte</option>
<option>Éducation artistique — Couture</option><option>EPS</option>
</select>
</div>
<div>
<label for="domaine">Domaine / sous-domaine</label>
<input id="domaine" placeholder="Domaine d'apprentissage">
</div>
<div>
<label for="duree">Durée totale (minutes) *</label>
<input id="duree" type="number" min="5" value="30" required>
</div>
<div class="full">
<label for="titre">Titre / notion de la leçon *</label>
<input id="titre" required placeholder="Ex. : Les diphtongues">
</div>
<div class="full">
<label for="competences">Compétence(s) visée(s)</label>
<textarea id="competences" placeholder="Compétences à développer chez les apprenants"></textarea>
</div>
<div class="full">
<label for="prerequis">Prérequis</label>
<textarea id="prerequis" placeholder="Connaissances que les apprenants doivent déjà posséder"></textarea>
</div>
<div class="full">
<label for="objectif">Objectif spécifique / résultat attendu *</label>
<textarea id="objectif" required placeholder="À la fin de la séance, l'apprenant sera capable de…"></textarea>
</div>
<div class="full">
<label for="situation">Situation d'apprentissage / situation-problème</label>
<textarea id="situation" placeholder="Situation concrète proposée aux apprenants"></textarea>
</div>
<div class="full">
<label for="materiel">Matériel didactique</label>
<textarea id="materiel" placeholder="Manuels, images, objets, tableau, ardoises…"></textarea>
</div>
<div class="full">
<label for="evaluation">Évaluation / exercices d'application</label>
<textarea id="evaluation" placeholder="Questions ou exercices pour vérifier les acquis"></textarea>
</div>
<div class="full">
<label for="remediation">Remédiation / consolidation</label>
<textarea id="remediation" placeholder="Activités pour aider les apprenants en difficulté et consolider les acquis"></textarea>
</div>
<div class="full">
<label for="projection">Retour / projection</label>
<textarea id="projection" placeholder="Bilan, réinvestissement ou annonce de la prochaine séance"></textarea>
</div>
<div class="full">
<label for="observations">Observations</label>
<textarea id="observations" placeholder="Difficultés rencontrées, ajustements à prévoir…"></textarea>
</div>
</div>

<div class="actions">
<button type="submit">Générer la fiche</button>
<button type="button" class="secondary" id="pdf">Imprimer / PDF</button>
<button type="reset" class="light">Effacer le formulaire</button>
</div>
</form>
</section>

<section class="panel" id="fiche">
<h2>FICHE DE PRÉPARATION PÉDAGOGIQUE</h2>
<div id="contenu"></div>
<div class="actions">
<button type="button" id="pdf2">Imprimer / PDF</button>
<button type="button" class="secondary" id="retour">Modifier la fiche</button>
</div>
</section>
</main>

<footer>Bot pédagogique APC Bénin — Outil d'aide à la préparation des séances.</footer>

<script>
const $ = id => document.getElementById(id);

function valeur(id){
 return $(id).value.trim();
}
function echapper(texte){
 return String(texte).replace(/[&<>"']/g, c => ({
  '&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'
 }[c]));
}
function ligne(label, id){
 const v = valeur(id);
 return v ? `<p class="info"><strong>${echapper(label)} :</strong> ${echapper(v)}</p>` : '';
}
function generer(){
 const duree = Math.max(5, Number(valeur('duree')) || 30);
 const phases = [
  {nom:'Mise en route',part:0.10,
   consigne:'Mobiliser les acquis antérieurs et annoncer la tâche.',
   activite:'Écoutent, répondent et se préparent.',
   resultat:'Les prérequis sont rappelés.'},
  {nom:'Découverte',part:0.15,
   consigne:'Présenter la situation d’apprentissage et poser le problème.',
   activite:'Observent, écoutent et identifient le problème.',
   resultat:'La situation est comprise.'},
  {nom:'Recherche',part:0.25,
   consigne:'Demander aux apprenants de chercher individuellement ou en groupe.',
   activite:'Cherchent, manipulent, échangent et proposent des solutions.',
   resultat:'Des propositions de réponses sont formulées.'},
  {nom:'Mise en commun',part:0.20,
   consigne:'Faire présenter les démarches et confronter les réponses.',
   activite:'Présentent leurs résultats et justifient leurs réponses.',
   resultat:'Les réponses sont comparées et discutées.'},
  {nom:'Structuration',part:0.15,
   consigne:'Guider la synthèse et faire formuler la règle ou la notion.',
   activite:'Formulent la règle, prennent note et donnent des exemples.',
   resultat:'La notion essentielle est formulée.'},
  {nom:'Évaluation',part:0.10,
   consigne:'Proposer une tâche individuelle de vérification.',
   activite:'Réalisent l’exercice et expliquent leur démarche.',
   resultat:'Les acquis sont vérifiés.'},
  {nom:'Bilan et projection',part:0.05,
   consigne:'Faire rappeler l’essentiel et annoncer la suite.',
   activite:'Rappellent ce qui a été appris.',
   resultat:'L’essentiel est retenu.'}
 ];
 let total = 0;
 const minutes = phases.map((p,i) => {
  if(i === phases.length-1) return duree-total;
  const m = Math.max(1,Math.round(duree*p.part));
  total += m;
  return m;
 });
 const phaseRows = phases.map((p,i)=>`
 <tr>
 <td>${echapper(p.nom)}</td>
 <td>${minutes[i]} min</td>
 <td>${echapper(p.consigne)}</td>
 <td>${echapper(p.activite)}</td>
 <td>${echapper(p.resultat)}</td>
 </tr>`).join('');

 const date = valeur('date');
 const dateAffichee = date ? new Date(date+'T12:00:00').toLocaleDateString('fr-FR') : '';
 $('contenu').innerHTML = `
 <table class="meta">
 <tr><td>École</td><td>${echapper(valeur('ecole')||'À compléter')}</td></tr>
 <tr><td>Enseignant(e)</td><td>${echapper(valeur('enseignant')||'À compléter')}</td></tr>
 <tr><td>Date</td><td>${echapper(dateAffichee||'À compléter')}</td></tr>
 <tr><td>Période</td><td>${echapper(valeur('periode')||'À compléter')}</td></tr>
 <tr><td>Classe</td><td>${echapper(valeur('classe'))}</td></tr>
 <tr><td>Discipline</td><td>${echapper(valeur('discipline'))}</td></tr>
 <tr><td>Domaine</td><td>${echapper(valeur('domaine')||'À préciser')}</td></tr>
 <tr><td>Leçon / notion</td><td><strong>${echapper(valeur('titre'))}</strong></td></tr>
 <tr><td>Durée totale</td><td>${duree} minutes</td></tr>
 </table>
 <h3>1. Compétences visées</h3>
 ${ligne('Compétence(s)','competences')||'<p>À préciser selon le programme applicable.</p>'}
 <h3>2. Prérequis</h3>
 ${ligne('Prérequis','prerequis')||'<p>À préciser.</p>'}
 <h3>3. Objectif spécifique / résultat attendu</h3>
 <p class="info">${echapper(valeur('objectif'))}</p>
 <h3>4. Situation d’apprentissage</h3>
 ${ligne('Situation proposée','situation')||'<p>À compléter par l’enseignant.</p>'}
 <h3>5. Matériel didactique</h3>
 ${ligne('Matériel','materiel')||'<p>À préciser selon la leçon.</p>'}
 <h3>6. Déroulement de la séance</h3>
 <table class="phases">
 <thead><tr><th>Phase</th><th>Durée</th><th>Consignes de l’enseignant</th><th>Activités des apprenants</th><th>Résultats attendus</th></tr></thead>
 <tbody>${phaseRows}</tbody>
 </table>
 <h3>7. Évaluation / application</h3>
 ${ligne('Activités proposées','evaluation')||'<p>Prévoir un exercice adapté à l’objectif de la séance.</p>'}
 <h3>8. Remédiation / consolidation</h3>
 ${ligne('Actions prévues','remediation')||'<p>Reprendre la notion avec des exemples ou exercices adaptés aux besoins observés.</p>'}
 <h3>9. Retour / projection</h3>
 ${ligne('Bilan et suite','projection')||'<p>Faire rappeler l’essentiel et prévoir le réinvestissement.</p>'}
 <h3>10. Observations</h3>
 ${ligne('Observations','observations')||'<p>À compléter après la séance.</p>'}
 <p class="info"><em>Document généré automatiquement. Vérifier et adapter les phases, les consignes et les contenus au programme officiel APC du Bénin et au niveau de la classe.</em></p>
 `;
 $('fiche').style.display='block';
 $('fiche').scrollIntoView({behavior:'smooth',block:'start'});
}
$('formulaire').addEventListener('submit',e=>{
 e.preventDefault();
 generer();
});
function imprimer(){
 if($('fiche').style.display!=='block'){
  if(!$('formulaire').reportValidity()) return;
  generer();
 }
 window.print();
}
$('pdf').addEventListener('click',imprimer);
$('pdf2').addEventListener('click',()=>window.print());
$('retour').addEventListener('click',()=>{
 $('formulaire').scrollIntoView({behavior:'smooth',block:'start'});
});
$('formulaire').addEventListener('reset',()=>{
 $('fiche').style.display='none';
});
</script>
</body>
</html>
