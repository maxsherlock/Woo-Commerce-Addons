Welcome!

//**For a WP plugin I've been developing I needed to change a plugin's value in functions.php (I'm thinking along the lines of a child theme), opposed to hard coding the actual plugin, to try and avoid issues on future updates. I just did it for an online dating company's gallery, which also increased load time speed.
Raw**//

So I'm focusing on the apply_filters method instead of changing core plugin code, this is what I did for the dating site's plugin.

// I use apply_filters() to allow a general override of values...
public static function loop_shop_per_page() {
    $value = get_option( 'posts_per_page' );
    return apply_filters('filter_loop_shop_per_page', $value);
}
Then, in WP functions.php (in the child theme), I'm able to select the value on for that by adding the necessary filter:

add_filter('filter_loop_shop_per_page', 'mytheme_loop_shop_per_page');

function mytheme_loop_shop_per_page($value){
    return -1;
}

===

Some examples of this in action:

 - [Wordpress Codex on Applying Filter](https://developer.wordpress.org/reference/functions/apply_filters/)
 - [Private Online Dating Gallery Plugin on Todd and Clare](https://www.toddandclare.com/gallery/) {My plugin developed for [Todd and Clare Dating](https://www.toddandclare.com/)}
 - [Another online dating plugin I developed](https://www.toddandclare.com/gallery/meagan-new-york-unlisted-4209686146/) {Use Ctrl + U to see line 382 of Code Dump for [USA MAP in Dating Gallery](https://www.toddandclare.com/search/)}

 	
In this case, setting the plugin's value globally, I could have also updated the database value for the plugin galley with update_option('images_per_page', -1);
