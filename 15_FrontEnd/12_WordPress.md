To load CSS file:
```html
<link rel="stylesheet" href="<?php echo get_stylesheet_uri(); ?>">
```
In order to use images, load them first.

To create page a template is needed. Template is considered by WordPress PHP file with header as below:
```php
<?php
/*
Template Name: Template Page
*/
?>

<?php get_header(); ?>

<?php get_footer(); ?>
```
