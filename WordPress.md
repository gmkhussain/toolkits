#WordPress Tips

###How display custom post type by categories
```html
$args = array(
	'post_type' => 'ourwork',
	'posts_per_page' => -1,
	'tax_query' => array(
		array(
			'taxonomy' => 'ourwork_categories',
			'field'    => 'slug',
			'terms'    => 'cs-i-softbank',
		),
	),
);
$query = new WP_Query( $args );
```