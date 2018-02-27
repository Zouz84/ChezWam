# README

*"Yo-Yo Salut youtube nous revoilà pour une nouv.."* ah non pardon. Bon bin, Salut à toi, Ô correcteur ! <br/>
<br/>
Alors sache que les 2 projets du jour sont intégrés dans une seule et même application. C'est pas magique ça? non? d'accord.<br/>
Quoi qu'il en soit, retrouve vite cette application ici: https://morning-meadow-21483.herokuapp.com/.
<br/>
<br/>
Tu y découvriras dans un premier temps: **Le projet TABULATION:**.<br/>
C'est du code de base, j'ai écris comme je pensais: bêtement.<br/>
    En 2 mots, j'ai organisé mes *div* de façon à ce qu'il y ait une **grosse** Div: "Container".<br/>
Cette div fait son taff, elle contient:<br/>
<br/>
**2** div:
* la Div **"titres"**, qui contient les 3 titres *Presentation* - *Menu* - *Services*.
* La Div **"textos"** qui envoie des Sms. Non, c'est pas la même chose. Div qui regroupe 3 **p**aragraphes de texte (soit *textun*, *textdeux*, *texttrois*). Chacun de ces paragraphes etant classés dans une div de classe **"un"**.
<br/>
La logique étant:<br/>

*"Bon j'arrive sur le site, il n'y a aucun **texte** de visible, seul les **titres** "*.<br/>
Du coup je `.hide()` mes 3 textes (à noter, j'annonce à Js que je vais utiliser du jQuery avec le fameux `$(document).ready(function() { blablabla });:` pour qu'il soit 'ready').
```JavaScript
$(document).ready(function() {
    $(".textun").hide();
    $(".textdeux").hide();
    $(".texttrois").hide();
```
(Lire: On *sélectionne* la classe nommée "textun", et on lui applique la fonction *hide*).<br/>
Ok bébé donc là quand on ouvre la page, les 3 paragraphes sont bien cachés, mais mes 3 titres (appelé class="pres", class="menu" et class="services") apparaissent bien. Cool c'est ce qu'on voulait.<br/>
Suite de la logique:<br/>
Quand je clique sur *(clickon)* un titre, je veux lui attitrer un texte, en gros je veux que tel paragraphe apparaisse au click, mais pas les autres ! Dans ce cas je précise la position de chacun de mes paragraphes: *toggle* ou *hide*.<br/>
**Remarque**: *Toggle* permet de *Show* au premier click, puis de *hide* en recliquant dessus.<br/>
ce qui nous donne, en jQuery:<br/>
```JavaScript
$(".pres").click(function() {
      $(".textun").toggle();
      $(".textdeux").hide();
      $(".texttrois").hide();
});
$(".menu").click(function() {
      $(".textun").hide();
      $(".textdeux").toggle();
      $(".texttrois").hide();
});
$(".services").click(function() {
      $(".textun").hide();
      $(".textdeux").hide();
      $(".texttrois").toggle();
});
});
```
Voilà du code bête et méchant. Qui nous permet de résoudre le probleme de tabulation.<br/>

Dans un Second temps, on se dit "mais où et doncor ni **Car**..**ousel** ?!":<br/>.
[Ici](https://www.w3schools.com/howto/howto_js_slideshow.asp).<br/>
Merci au revoir.<br/>
<br/>
<br/>
PS: J'ai pas mis le truc qui fais passer les Slides automatiquement, parceque je trouve pas ça beau, ni cool. Mais sinon, il suffisait apparemment de remplacer la fin du code par:<br/>
```JavaScript
var slideIndex = 0;
showSlides();

function showSlides() {
    var i;
    var slides = document.getElementsByClassName("mySlides");
    for (i = 0; i < slides.length; i++) {
        slides[i].style.display = "none"; 
    }
    slideIndex++;
    if (slideIndex > slides.length) {slideIndex = 1} 
    slides[slideIndex-1].style.display = "block"; 
    setTimeout(showSlides, 2000); // Change image every 2 seconds
}
```
Pour finir, je vais parler du début...<br/>
Pour lancer **jQuery**, il suffit de mettre un lien CDN dans notre **head** du *app/views/layouts/appliation.html.erb. soit: `<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>`.<br/>
Un peu de **CSS**, ici placé dans le fichier **main.css** du *app/assets/images/*.<br/>
Réaliser notre **asset pipeline**. Pour cela, modifier la ligne 31 de notre fichier *production.rb* situé en */config/environments/* et remplacer cette ligne 31 par : `  config.serve_static_assets = true
  config.assets.compile = true`.<br/>
Ajouter aussi: `Rails.application.config.assets.precompile += %w( main.css )` dans *assets/initializer/assets.rb*.<br/>
Enfin, n'oubliez pas de mettre vos images dans le dossier **Images** de votre dossier *assets*.<br/>
Et de faire un petit `rake:assets precompile` dans votre console.<br/>
<br/>
<br/>
**Force et Honneur !**
