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



###Email in HTML format in WordPress
```html
get_header();

$msg = '';

if($_REQUEST['submit'] == "my_from" ) {		//<form method="POST" name="my_from" action="#">
	$name_d = $_REQUEST['dname'];
	$email_d = $_REQUEST['demail'];
	$university_d = $_REQUEST['duniversity'];
	
		global $wpdb; //Insert data to DB 
	$wpdb->insert('bo_paycheck_downloader', array(
	'name' => $name_d,
    'email' => $email_d,
    'university_affiliation' => $university_d,
));
	
	
	
$to      = 'myemail@yahoo.com';
$subject = 'Email from WP';
$message = '
<html> 
  <body> 
    <p style="text-align:center;height:100px;background-color:#abc;border:1px solid #456;border-radius:3px;padding:10px;">
        <b>I am receiving HTML email</b>
        <br/><br/><br/><a style="text-decoration:none;color:#246;" href="www.example.com">example</a>
    </p>
    <br/><br/>Now you Can send HTML Email
  </body>
</html>';

$headers  = 'MIME-Version: 1.0' . "\r\n";
$headers .= 'Content-type: text/html; charset=iso-8859-1' . "\r\n";
$headers .= "From: info@test.net\r\n"."X-Mailer: php";

mail($to, $subject, $message, $headers);

	$msg = 'Thank You!';
	
	header('location: http://mydomain.com/ext-url');
}
```