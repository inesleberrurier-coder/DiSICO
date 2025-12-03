<script>
// Date du jour réel
const today = new Date();
const currentDay = today.getDate(); // Numéro du jour : 1,2,3...

// Générer les cases 1 à 24
const calendar = document.getElementById('calendar');
for(let i=1;i<=24;i++){
  const dayDiv = document.createElement('div');
  dayDiv.className = 'day';

  // Si le jour n'est pas encore arrivé → case verrouillée
  if(i > currentDay){
    dayDiv.classList.add("locked");
    dayDiv.innerHTML = i + " 🔒";
  } else {
    dayDiv.textContent = i;
    dayDiv.onclick = () => openPopup(i);
  }

  calendar.appendChild(dayDiv);
}

// Neige en fond
(function(){
  const count=80;
  for(let i=0;i<count;i++){
    const el=document.createElement('div');
    el.className='snowflake';
    el.textContent='❄';
    el.style.left=Math.random()*100+'vw';
    el.style.opacity=0.4+Math.random()*0.6;
    el.style.fontSize=(8+Math.random()*18)+'px';
    el.style.animationDuration=(6+Math.random()*8)+'s';
    document.body.appendChild(el);
  }
})();

// Popup
function openPopup(day){
  const box=document.getElementById('popupContent');
  box.innerHTML='';
  for(let i=0;i<30;i++){
    const f=document.createElement('div');
    f.className='popupSnowflake';
    f.textContent='❄';
    f.style.left=Math.random()*440+'px';
    f.style.animationDuration=4+Math.random()*4+'s';
    box.appendChild(f);
  }

  switch(day){
    case 1: box.innerHTML+=`<h2>Jour 1</h2><p><strong style='color:red;'>Info du Jour🗞️</strong> La DiSI CO a été <strong>parmi les premiers</strong> établissements à mettre en place l'intranet ULLO.</p>`; break;
    case 2: box.innerHTML+=`<h2>Jour 2</h2><p><strong style='color:red;'>Quiz :</strong> Savez-vous par qui a été développé l'outil TaToo météo ?</p>
      <form id='quiz2'><label><input type='radio' name='ans2' value='Nantes'> Nantes</label><br>
      <label><input type='radio' name='ans2' value='Angers'> Angers</label><br>
      <label><input type='radio' name='ans2' value='Rennes'> Rennes</label><br>
      <button type='button' onclick='checkQuiz("quiz2","Angers","res2","info2")'>Valider</button></form>
      <p id='res2'></p>
      <p id='info2' style='display:none;'>TaToo météo a été déployé à l'échelle nationale sur environ 120 000 postes entre mars et mai 2025.</p>`; break;

    case 3: box.innerHTML+=`<h2>Jour 3</h2><p><strong style='color:red;'>Info du Jour</strong> Tous les ans l'ESI d'Orléans participe au Cross de Bercy. Cette année :<br>
🏆 Nicolas 5km 322ème<br>
🏆 Eric 10km 630ème<br>
🏆 Charles-Etienne 10km 127ème<br>
👏 Bravo à eux et aux 2000 coureurs !</p>`; break;

    case 4: box.innerHTML+=`<h2>Jour 4</h2><p>Le site des Marsauderies accueille chaque année des nouveaux moutons 🐑</p>
      <form id='quiz4'><label><input type='radio' name='ans4' value='1'> 1</label><br>
      <label><input type='radio' name='ans4' value='2'> 2</label><br>
      <label><input type='radio' name='ans4' value='3'> 3</label><br>
      <button type='button' onclick='checkQuiz("quiz4","3","res4","info4")'>Valider</button></form>
      <p id='res4'></p>`; break;

    case 5: box.innerHTML+=`<h2>Jour 5</h2><p><strong style='color:red;'>Quiz :</strong> En quelle année l’IA a été créée ?</p>
      <form id='quiz5'><label><input type='radio' name='ans5' value='1956'> 1956</label><br>
      <label><input type='radio' name='ans5' value='1962'> 1962</label><br>
      <label><input type='radio' name='ans5' value='1970'> 1970</label><br>
      <button type='button' onclick='checkQuiz("quiz5","1956","res5","info5")'>Valider</button></form><p id='res5'></p>`; break;

    case 6: box.innerHTML+=`<h2>Jour 6</h2><p>Recette apéro : <a href='https://www.marmiton.org/recettes/recette_sapin-feuillete-au-pesto_383379.aspx' target='_blank'>Sapin feuilleté au pesto</a></p>`; break;

    case 7: box.innerHTML+=`<h2>Jour 7</h2><p>Recette apéro : <a href='https://www.marmiton.org/recettes/recette_gougeres-au-fromage_20095.aspx' target='_blank'>Gougères au fromage</a></p>`; break;

    case 8: box.innerHTML+=`<h2>Jour 8</h2><p>Contenu à ajouter.</p>`; break;

    case 9: box.innerHTML+=`<h2>Jour 9</h2><p>Contenu à ajouter.</p>`; break;

    case 10: box.innerHTML+=`<h2>Jour 10</h2><p>Contenu à ajouter.</p>`; break;

    case 11: box.innerHTML+=`<h2>Jour 11</h2><p>Contenu à ajouter.</p>`; break;

    case 12: box.innerHTML+=`<h2>Jour 12</h2><p><strong>En lumière :</strong> Nous avons 2 ruches aux Marsauderies pour la biodiversité 🍯🐝 et nous avons reçu des pots de miel.<p>Quiz : à votre avis, combien une abeille produit-elle de miel au cours de sa vie ? (g)</p>
      <input type="text" id="quiz12Input" placeholder="Votre réponse">
      <button type="button" onclick="checkOpenAnswer12()">Valider</button>
      <p id="quiz12Result"></p>`; break;

    case 13: box.innerHTML+=`<h2>Jour 13</h2><p>Recette : <a href='https://www.marmiton.org/recettes/recette_huitres-gratinees-au-parmesan_56242.aspx' target='_blank'>Huîtres gratinées</a></p>`; break;

    case 14: box.innerHTML+=`<h2>Jour 14</h2><p>Marchés de Noël en Loire-Atlantique : <a href='https://44.kidiklik.fr/articles/335276-les-marches-de-noel-nantes-et-en-loire-atlantique.html' target='_blank'>Voir la liste</a></p>`; break;

    case 15: box.innerHTML+=`<h2>Jour 15</h2><p>Relamping des néons remplacés par LED 💡 Cette démarche s'inscrit dans la politique <strong>ÉcoFiP</strong> de la direction<p>une vraie action écologique : réduction de la consommation électrique et moins de déchets.</p>`; break;

    case 16: box.innerHTML+=`<h2>Jour 16</h2><p>Contenu à ajouter.</p>`; break;

    case 17: box.innerHTML+=`<h2>Jour 17</h2><p>Concours des pulls de Noël le 19 décembre 🎅 ! Venez avec vos plus beaux pulls et gagnez vos chocolats 🍫 ! Nous prendrons une photo pour le vote final 📸.</p>`; break;
    case 18: box.innerHTML+=`<h2>Jour 18</h2><p>Contenu à ajouter.</p>`; break;

    case 19: box.innerHTML+=`<h2>Jour 19</h2><p>Journée mondiale du pull de Noël 🎄</p>
      <form id='quiz19'><label><input type='radio' name='ans19' value='France'> France</label><br>
      <label><input type='radio' name='ans19' value='Suisse'> Suisse</label><br>
      <label><input type='radio' name='ans19' value='Angleterre'> Angleterre</label><br>
      <button type='button' onclick='checkQuiz("quiz19","Angleterre","res19","info19")'>Valider</button></form>
      <p id='res19'></p>
      <p id='info19' style='display:none;'>La tradition vient d'Angleterre en 1980.</p>`; break;

    case 20: box.innerHTML+=`<h2>Jour 20</h2><p>Vin chaud : <a href='https://www.marmiton.org/recettes/recette_vin-chaud-aux-epices_25224.aspx' target='_blank'>Vin chaud aux épices</a></p>`; break;

    case 21: box.innerHTML+=`<h2>Jour 21</h2><p>Repas chaud : <a href='https://www.marmiton.org/recettes/recette_gratin-dauphinois_13809.aspx' target='_blank'>Gratin dauphinois</a></p>`; break;

    case 22: box.innerHTML+=`<h2>Jour 22</h2><p>Contenu à ajouter.</p>`; break;

    case 23: box.innerHTML+=`<h2>Jour 23</h2><p>Contenu à ajouter.</p>`; break;

    case 24: box.innerHTML+=`<h2>Jour 24</h2><p>Contenu à ajouter.</p>`; break;
  }

  document.getElementById('popup').style.display='block';
}

function closePopup(){
  document.getElementById('popup').style.display='none';
}

function checkQuiz(formId, correct, resId, infoId){
  const form=document.getElementById(formId);
  const selected=form?form.querySelector('input[type=radio]:checked'):null;
  const res=document.getElementById(resId);
  if(!res) return;
  if(!selected){ res.textContent='Sélectionnez une réponse !'; return; }
  if(selected.value===correct) res.textContent='Bonne réponse ! 👏';
  else res.textContent=`Loupé ! La bonne réponse est ${correct}.`;
  if(infoId){ const el=document.getElementById(infoId); if(el) el.style.display='block'; }
}

function checkOpenAnswer12(){
  const v=document.getElementById('quiz12Input').value.trim();
  const r=document.getElementById('quiz12Result');
  if(!r) return;
  if(!v) { r.textContent='Veuillez entrer une réponse.'; return; }
  r.innerHTML='Réponse : une abeille ne produit qu\'1/12 de cuillère à café de miel, soit environ 7 grammes.';
}
</script>
