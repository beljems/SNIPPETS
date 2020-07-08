### WORDPRESS | PHP

### PLUGINS

```sh
* Category Order and Taxonomy Terms Order Plugin to Wordpress
-order category

* WP SUPER CACHE
-for gzip > advanced > check compress

* CPT UI
-Wordpress plugin for creating post types

* Addquicktags
-add quick tags on page editor
```

### DEFINE OPTION URLS

```sh
define( 'WP_HOME', 'http://localhost' );
define( 'WP_SITEURL', 'http://localhost' );
```

### GLOBAL $post

```sh
Please use setup_postdata() and wp_reset_postdata() when you use
global $post so it would not cause conflict on the existing global $post.

global $post;
$post = $article_item; // Assign your post details to $post (& not any other variable name!!!!)
setup_postdata( $post );

<?php wp_reset_postdata(); ?>
```

### Get Ordinal and days in JP
```sh
<?php

function ordinal($number) {
    $ends = array('th','st','nd','rd','th','th','th','th','th','th');
    if ((($number % 31) >= 11) && (($number % 31) <= 13)) {
        return 'th';
    } else {
        return $ends[$number % 10];
    }
}

function daysInJP($event) {
    $sched_day = $event->format('D');

    switch($sched_day) {
      case 'Mon':
        echo '（月）';
        break;
      case 'Tue':
        echo '（火）';
        break;
      case 'Wed':
        echo '（水）';
        break;
      case 'Thu':
        echo '（木）';
        break;
      case 'Fri':
        echo '（金）';
        break;
      case 'Sat':
        echo '（土）';
        break;
      case 'Sun':
        echo '（日）';
        break;
      default:
        echo '';
    }
}
```

### Date Filter in Wordpress
```sh
function get_news_years() {
    $args = array(
        'post_type' => NEWS_POST_TYPE,
        'order' => 'DESC',
        'post_status' => 'publish',
        'posts_per_page' => -1,
    );

    $news_query = new WP_Query( $args );

    foreach( $news_query->posts as $news_year ) {
        $post_years[] = date( 'Y', strtotime( $news_year->post_date ));
    }

    return array_unique( $post_years );
}
```

### Creating one or more options inside functions
```sh
// acf optionページの設定
if( function_exists('acf_add_options_page') ) {

    acf_add_options_page(array(
        'page_title' => 'Common Footer',
        'menu_title'=> 'Common Footer',
        'menu_slug' => 'common_footer',
        //'capability'=> 'edit_posts',
        'redirect'=> false
    ));

    acf_add_options_page(array(
        'page_title' => 'Common Footer',
        'menu_title'=> 'Common Footer',
        'menu_slug' => 'common_footer',
        //'capability'=> 'edit_posts',
        'redirect'=> false
    ));

}

Creating function and field is in options, add `options` inside `get_field`,
Calling direct field that not inside the options `get_field( 'mv_background' );`

function get_footer_details() {
    $footer_logo = get_field( 'footer_logo', 'options' );
    $footer_contact_address = get_field( 'footer_contact_address', 'options' );
    $footer_telephone_number = get_field( 'footer_telephone_number', 'options' );
    $footer_fax_number = get_field( 'footer_fax_number', 'options' );
    $footer_banners = get_field( 'footer_banners', 'options' );
    $footer_args = array(
    'footer_logo' => $footer_logo,
    'footer_contact_address' => $footer_contact_address,
    'footer_telephone_number' => $footer_telephone_number,
    'footer_fax_number' => $footer_fax_number,
    'footer_banners' => $footer_banners,
    );
    return $footer_args;
}
```

### Calling parent page title

```sh
<?php
  global $post;
  setup_postdata( $post );

  echo get_the_title( $post->post_parent );

  wp_reset_postdata();
?>
```

### REMOVING ADMIN ELEMENTS USING PHP HOOK

```sh
if (!has_action('admin_footer', 'alert_category')) {
    //	add_action( 'admin_footer' , 'lig_wp_alert_unselected_category' );
  add_action( 'admin_footer' , 'wp_acf_hide_remove_option' );
}

function wp_acf_hide_remove_option()
{
  echo <<< EOF
  <script type="text/javascript">

    const aboutStaffsRemove = document.querySelectorAll('#acf-group_5e201adc5dfcd .remove');

    aboutStaffsRemove.forEach(function(e) {
      e.style.display = 'none';
    });

  </script>';
  EOF;
}
```

### RELATED POST on SINGLE

```sh
function get_related_posts($post_id) {
  $args = array(
    'post_type'        => get_post_type(), //default function to get post type
    'post__not_in'     => array($post_id),
    'posts_per_page'   => 3,
    'order'            => 'ASC',
    'hide_empty'       => true,
  );

  return new WP_Query($args);
}
```

### STRIP VERY LONG CONTENT
```sh
<?php echo mb_substr(wp_strip_all_tags(get_the_content()), 0, 100); ?>
```

```sh
$count = 0; // 0+1
foreach($schedule_tabs as $tab) :
$count++;
echo $count; // 1
endforeach;

if($sched_count1 > 1) {
   break;
 } // stop the loop if count greater 1;
```

```sh
$schedule_tabs[0]['tab'] // accessing array within array
array_slice($schedule_tabs, 1) // starts loop at the second value
```

### GET THE CURRENT TAG BY ID

```sh
$get_tag_id = get_queried_object()->term_id;
$get_term_by = get_term_by('id', $get_tag_id, NEWS_TAX_TAG);
$categorySlug = $get_term_by->slug;
```

```sh
$post_id = get_the_ID(); // or use the post id if you already have it
$category_object = get_the_category($post_id); // post id
$category_name = $category_object[0]->name; // category name
$category_id = get_cat_ID($category_name); // get category id
```

### GET THE TAG
```sh
$get_tag_id = get_queried_object()->term_id;
$get_term_by_tag = get_term_by('id', $get_tag_id, BLOG_CAT);
$tagName = $get_term_by_tag->name;
```

### GET THE CATEGORY NAME
```sh
$get_term_bg_category = get_the_terms($post->ID, BLOG_CAT);
$categoryName = $get_term_bg_category->name;
```
