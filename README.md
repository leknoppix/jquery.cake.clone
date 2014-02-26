# jquery.cake.clone

A simple jQuery plugin to clone inputs generated via CakePHP.

## Installation

Include the script * after * the Jquery librairy.

```html
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
<script src="/path/to/jquery.cake.clone.js"></script>

```

## How to

Suppose we have this as instruction in php (of course linked to the CakePHP framework):

```php
<div class="body-0">
<?php 
	echo $this->Form->input('0.name');
?>
</div>
<a href="#" class="addproduct">Add a new product</a>

```

We get source code HTML:

```html
<div class="body-0">
<div class="input text"><label for="Controller0Name">Name</label><input name="data[Controller][0][name]" type="text" id="Controller0Name"/></div></div>
<a href="#" class="addproduct">Add a new product</a>

```

So that the successful cloning correctly, we launched cloning when clicking on the link with the class selector called *addproduct*. We need to use the extension jquery.cake.clone accompanied with options to clone the fields selected.
Here is an example call:

```javascript
$(function() {
	var options = {
    	init:'0',
    	nbrincrem:'0',
    	classclone:'body-',
    	controller:'Controller',
  	}
	$('.addproduct').on('click',function()
	{
		$(this).clonage(options);
	});
});

```

When running a cloning, we get:
```html
<div class="body-0">
<div class="input text"><label for="Controller0Name">Name</label><input name="data[Controller][0][name]" type="text" id="0Name"/></div>
</div>
<div class="body-1">
<div class="input text"><label for="Controller1Name">Name</label><input name="data[Controller][1][name]" type="text" id="Controller1Name"/></div>
</div>
<a href="#" class="addproduct">Add a new product</a>

```

The options array contains several parameters.
* The first parameter *init* identifies the master div (the div to clone).
* The second parameter *nbrincrem* must be the same as the launch of * init* and will increment each time you add the number of the clone made​​..
* The third parameter *classclone* specifies the name of the div to be cloned without its identification number.
* The last parameter *controller* is used to specify the name of the controller.

## Evolution

This plugin is simple, it may evolve progressively uses and returns. 
To meet any problem, do not hesitate to use the wiki to return your ideas. 
Thank you in advance.
