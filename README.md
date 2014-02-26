# jquery.cake.clone

Un simple jQuery plugin pour cloner les inputs générés via cakePhp.

## Installation

Inclure le script *après* la librairy Jquery

```html
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
<script src="/path/to/jquery.cake.clone.js"></script>
```
## Usage

Supposons que nous avons ceci comme instruction en php (lié biensûr au framework cakePhp):

```php
<div class="body-0">
<?php 
	echo $this->Form->input('0.name');
?>
</div>
<a href="#" class="addproduct">Ajouter un produit</a>
`̀`

Nous obtiendrons en code source HTML:

```html
<div class="body-0">
<div class="input text"><label for="0Name">Name</label><input name="data[0][name]" type="text" id="0Name"/></div></div>
<a href="#" class="addproduct">Ajouter un produit</a>
̀``

Afin que le clonage réussisse correctement, nous allons lancé le clonage lors du click sur le lien présentant le select class appelé *addproduct*. Nous devons donc faire appel à l'extension jquery.cake.clone accompagné avec des options afin de cloner le ou les champs selectionnés.
Voici un exemple d'appel:

```javascript
$(function() {
	var options = {
    	init:'0',
    	nbrincrem:'0',
    	classclone:'body-',
    	controller:'Openform',
  	}
	$('.addproduct').on('click',function()
	{
		$(this).clonage(options);
		$('.body-'+options.nbrincrem+' input').val('');
		$('.body-'+options.nbrincrem+' input.calcul').val('0');
	});
});
```

Lors de l'exécution d'un clonage, nous obtiendrons:
```html
<div class="body-0">
<div class="input text"><label for="0Name">Name</label><input name="data[0][name]" type="text" id="0Name"/></div>
</div>
<div class="body-1">
<div class="input text"><label for="0Name">Name</label><input name="data[1][name]" type="text" id="1Name"/></div>
</div>
<a href="#" class="addproduct">Ajouter un produit</a>
̀``