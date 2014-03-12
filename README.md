# jquery.cake.clone

A simple jQuery plugin to clone inputs generated via CakePHP.

## Installation

Make sure you include the script *after* the jQuery library.

```html
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.9.1/jquery.min.js"></script>
<script src="/path/to/jquery.cake.clone.js"></script>

```

## How to

Suppose we have this instruction in php (of course linked to the CakePHP framework):

```php
<div class="body-0">
<?php 
	echo $this->Form->input('0.name');
?>
</div>
<a href="#" class="addproduct">Add a new product</a>

```

This yields the following HTML code:

```html
<div class="body-0">
<div class="input text"><label for="Controller0Name">Name</label><input name="data[Controller][0][name]" type="text" id="Controller0Name"/></div></div>
<a href="#" class="addproduct">Add a new product</a>

```

To ensure successful cloning, we trigger the cloning process by clicking the link that has the class selector called *addproduct*. We need to use the jquery.cake.clone extension together with the necessary options to clone the selected fields.
Here is an example call:

```javascript
$(function() {
	var options = {
    	init:0,
    	nbrincrem:0,
    	delimiter:'-',
    	classclone:'body',
    	controller:'Controller',
  	}
	$('.addproduct').on('click',function()
	{
		$(this).clonage(options);
	});
});

```

After successful cloning, we get:
```html
<div class="body-0">
<div class="input text"><label for="Controller0Name">Name</label><input name="data[Controller][0][name]" type="text" id="0Name"/></div>
</div>
<div class="body-1">
<div class="input text"><label for="Controller1Name">Name</label><input name="data[Controller][1][name]" type="text" id="Controller1Name"/></div>
</div>
<a href="#" class="addproduct">Add a new product</a>

```

The options object contains several parameters.
* The first parameter *init* identifies the master div (the div to clone).
* The second parameter *nbrincrem* must be identical to *init*, and will increment each time you add a new clone.
* The third parameter *classclone* specifies the name of the div to be cloned without its identification number.
* The last parameter *controller* is used to specify the name of the controller.

## Evolution

This plugin is still basic, it may evolve with reports and feedbacks. 
Should you have any problem, question or inquiry, please do not hesitate to use the wiki and to share your ideas. 
Thanks!
