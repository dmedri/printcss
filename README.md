# printcss
Helpful tools and tips to support web printing

## Introduction

Publishing content intended for on-screen reference often overlooks
the presence of style sheets suitable for printing. It often happens
on the web or in themes intended for the main applications in use (e.g. wordpress).

To have a personal memory and to be able to offer a contribution or
a simple reference to those who want to change the state of the art, 
I collect here some useful examples.

Header code:

```html
<link href="style.css" media="screen" rel="stylesheet"/>
<link href="print.css" media="print" rel="stylesheet"/>
```

## Wordpress tips

In functions.php:

```php
<?php                                                                                                                                                     
function theme_enqueue_styles() {
    global $wp_version;
    wp_enqueue_style( 'parent-style', get_template_directory_uri() . '/style.css' ); 
    wp_enqueue_style( 'child-style', get_stylesheet_directory_uri() . '/style.css', array('parent-style') ); 
    wp_enqueue_style( 'child-style-print', get_stylesheet_directory_uri() . '/print.css', array(), $wp_version, 'print' ); 
}
add_action( 'wp_enqueue_scripts', 'theme_enqueue_styles' , 100);
?>
```

## Bibliography

1. https://developer.mozilla.org/en-US/docs/Web/Guide/Printing
2. https://www.w3schools.com/css/css3_mediaqueries.asp
3. https://codex.wordpress.org/Styling_for_Print
