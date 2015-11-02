# Un peu de sécurité pour [herobrine.fr](http://herobrine.fr)

Tout est ici Behel ~

###À rajouter dans le fichier html :
``` html
<!--Pour chaque bouton de suppression-->
<BaliseRandom id="IdDuTrucÀSupprimer" class="del_button"></BaliseRandom>
  
<!--Une fois par fichier-->
<form action="PageDeTraitement" method="POST" id="js_form">
  <input type="hidden" id="js_form_id" name="Id" value="" />
  <input type="hidden" name="Action" value="ActionÀFaire" />
</form>
```
Tous les noms commençant par une majuscule **sont à remplacer** par ce qui t'arrange.

###À rajouter dans un fichier js : 
* **S'IL Y A BESOIN D'UNE CONFIRMATION**
``` javascript
var form = document.getElementById("js_form");
var id_param = document.getElementById("js_form_id");
var list = document.getElementsByClassName("del_button");
  
for (var i =0; i < list.length; i++) {
  list[i].addEventListener('click', function (e) {
    if(confirm("Êtes-vous sûr de vouloir suprimer ce message ?")) {
      id_param.value = e.target.id;
      form.submit();
    }
  }, false)
}
```
* **S'IL N'Y A PAS BESOIN D'UNE CONFIRMATION**
``` javascript
var form = document.getElementById("js_form");
var id_param = document.getElementById("js_form_id");
var list = document.getElementsByClassName("del_button");
  
for (var i =0; i < list.length; i++) {
  list[i].addEventListener('click', function (e) {
    id_param.value = e.target.id;
    form.submit();
  }, false)
}
```

###Pour le PHP
Bah les "GET" à remplacer par "POST", et les noms des champs à adapter d'un côté ou de l'autre. Je ne sais pas trop comment c'est organisé ^^'

J'espère que ça te donnera la motivation de sécuriser un peu ton superbe site ;3
