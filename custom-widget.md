<?php
/*
Plugin Name: Widget bypassing functions.php
Plugin URI: https://gist.github.com/maxsherlock/
Description: Create a custom widget in wordpress bypassing the functions.php
Author: Max Sommers
Contributors: maxsherlock
Author URI: https://gist.github.com/maxsherlock/
Version: 1.0
/*
/**
 * Create custom widget class. You will need to add the on page html in form code at the end.
 */
class My_Widget extends WP_Widget {

   ob_start();
    .
    .
    .
   $page = ob_get_contents();
   $fp = fopen("output.html","w");
   fwrite($fp,$page);
   ob_end_flush();
   fclose($fp);
 ?>
    /**
    * Sets up the custom widget name etc
    */
    public function __construct() {
     // widget actual processes
    }

   /**
   * Outputs the content of the custom widget
   *
   * @param array $args
   * @param array $instance
   */
   public function widget( $args, $instance ) {
    // outputs the content of the custom widget
   }

  /**
  * Outputs the options form on admin
  *
  * @param array $instance The custom widget options
  */
  public function form( $instance ) {
    // outputs the options form on admin
  }

  /**
  * Processing custom widget options on save
  *
  * @param array $new_instance The new options
  * @param array $old_instance The previous options
  */
  public function update( $new_instance, $old_instance ) {
    // processes widget options to be saved
  }
}  
/*
// Start by adding the following to your page where you want the widget to appear: // 

<form method='post' action="custom-widget.php"> <p class="submit">   
<input type="submit" class="button-primary"    value="submit" /> 
</p> </form>    

// Create a new php file entitled custom-widget.php in your CHILD theme wp-content directory

Some background on this custom widget plugin and an example:

 - [Handling Wordpress API](https://codex.wordpress.org/Widgets_API)
 - [Todd and Clare](https://www.toddandclare.com) {Search page custom widget plugin I submitted on [Dating Registration Page](https://www.toddandclare.com/register-free/)}
 - /*
