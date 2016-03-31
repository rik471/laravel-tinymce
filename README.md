##TinyMCE editor for Laravel and Lumen Framework
Powerful WYSIWYG editor with easy installation and already configured to use quickly and simply.

[![Latest Stable Version](https://poser.pugx.org/ktquez/laravel-tinymce/v/stable)](https://packagist.org/packages/ktquez/laravel-tinymce) [![Total Downloads](https://poser.pugx.org/ktquez/laravel-tinymce/downloads)](https://packagist.org/packages/ktquez/laravel-tinymce) [![Latest Unstable Version](https://poser.pugx.org/ktquez/laravel-tinymce/v/unstable)](https://packagist.org/packages/ktquez/laravel-tinymce) [![License](https://poser.pugx.org/ktquez/laravel-tinymce/license)](https://packagist.org/packages/ktquez/laravel-tinymce)

If you want to be available globally, just add the tag ``<head>``

## Instalation
```shell
composer require ktquez/laravel-tinymce 
```

## Laravel
Add in ``config/app.php``: <br>
```php
'Ktquez\Tinymce\TinymceServiceProvider'

// or

Ktquez\Tinymce\TinymceServiceProvider::class
```

Finally, publish the files: <br>
```shell
php artisan vendor:publish --force
```

## Lumen
Add in ``bootstrap/app.php``: <br>
```php
$app->configure('tinymce');
$app->register('Ktquez\Tinymce\TinymceServiceProvider');
```

As in Lumen can not run the ``vendor:publish``, you must copy the ``config/tinymce.php`` to the base path of your project in the ``config/``

And copy the ``tinymce/`` folder that is within ``assets/js/`` to your folder ``public/`` with the path you want.

## How to use
Just add the line in his view, well above the ``<textarea class="tinymce">``:<br>
```php
@include('tinymce::tpl')  
```


### Custom configuration to each textarea
Just go in the configuration file ``config/tinymce.php``, create a key in the settings through the array, there is an example of how to create settings for each textarea.
For example: 
```php
return [

...

	'myTxt1' => [
		"selector" => ".myTxt1",
		"language" => 'en',
		"theme" => "modern",
		"skin" => "lightgray",
		"plugins" => [
			...
		],
		"toolbar" => "insertfile undo redo | styleselect | bold italic | alignleft aligncenter alignright alignjustify | bullist numlist outdent indent | l      ink image | print preview media fullpage | forecolor backcolor emoticons",
	],
		
	'myTxt2' => [
		"selector" => ".myTxt2",
		"language" => 'en',
		"theme" => "modern",
		"skin" => "lightgray",
		"plugins" => [
			...
		],
		"toolbar" => "ink image | print preview media fullpage | forecolor backcolor emoticons",
	],

]
```

In his view, when using the include, you must pass an array ``els``  through each key.
```php 
@include('tinymce::tpl', ['els' => ['myTxt1', 'myTxt2']]);
```

## Path of script

In ``config/tinymce.php`` have the settings of your editor: <br>
Set the path of ``tinymce.min.js`` file:
```
'cdn' => config('app.url').'/vendor/js/tinymce/tinymce.min.js',
```

### Customization

Set customization parameters of TinyMCE:
Set the ``id`` or ``class``  of the textarea
```
'default' => [
		"selector" => ".tinymce",
		...
```

Sets the language editor, available in the package ``de, es, pt_BR and fr_FR``
```
"language" => 'pt_BR',
```

Skin editor, available in the package ``lightgray, charcoal and tundora``
```
"skin" => "lightgray",
```

Add plugins and toolbar, by default:
```
"plugins" => [
    "advlist autolink link image lists charmap print preview hr anchor pagebreak spellchecker",
    "searchreplace wordcount visualblocks visualchars code fullscreen insertdatetime media nonbreaking",
    "save table contextmenu directionality emoticons template paste textcolor"
	  ],
"toolbar" => "insertfile undo redo | styleselect | bold italic | alignleft aligncenter alignright alignjustify | bullist numlist outdent indent | l      ink image | print preview media fullpage | forecolor backcolor emoticons",
```

##### To learn more, just access the [TinyMCE](https://www.tinymce.com/docs/) documentation 
TinyMCE : Current Version [4.3.8](https://www.tinymce.com/download/) 











