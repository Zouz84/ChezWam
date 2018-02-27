# README

*"Yo-Yo Salut youtube nous revoilà pour une nouv.."* ah non pardon. Bon bin, Salut à toi, Ô correcteur ! <br/>
<br/>
Alors sache que les 2 projets du jour sont intégrés dans une seule et même application. C'est pas magique ça? non? d'accord.<br/>
Quoi qu'il en soit, retrouve vite cette application ici: https://morning-meadow-21483.herokuapp.com/.
<br/>
Tu y découvriras dans un premier temps: **Le projet TABULATION:**.<br/>
C'est du code de base, j'ai écris comme je pensais: bêtement.<br/>
    En 2 mots, j'ai organisé mes *div* de façon à ce qu'il y ait une **grosse** Div: "Container".<br/>
Cette div fait son taff, elle contient!<br/>
<br/>
Elle contient **2** div:
* la Div **"titres"**, qui contient les 3 titres *Presentation* - *Menu* - *Services*.
* La Div **"textos"** qui envoie des Sms. Non, c'est pas la même chose. Div qui regroupe 3 **p**aragraphes de texte (soit *textun*, *textdeux*, *texttrois*). Chacun de ces paragraphes etant classés dans une div de classe **"un"**.
<br/>
La logique étant:<br/>
*"-Bon j'arrive sur le site, il n'y a aucun **texte** de visible, seul les **titres**"*.<br/>
Du coup je `.hide()` mes 3 textes (à noter, j'annonce à Js que je vais utiliser du jQuery avec le fameux `$(document).ready(function() { blablabla });:` pour qu'il soit 'ready').
```JavaScript
$(document).ready(function() {
    $(".textun").hide();
    $(".textdeux").hide();
    $(".texttrois").hide();
```
Ok bébé donc là quand on ouvre la page, les 3 paragraphes sont bien cachés, mais mes 3 titres (appelé class="pres", class="menu" et class="services") apparaissent bien. Cool.<br/>


Sinon il suffit de rajouter
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
à la suite de notre code jQuery pour que ça avance automatiquement
