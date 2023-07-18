# printcss
Helpful tools and tips to support web printing

## Introduction

Header code:

```html
<link href="style.css" media="screen" rel="stylesheet" />                                                                                       
<link href="print.css" media="print" rel="stylesheet" />
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
