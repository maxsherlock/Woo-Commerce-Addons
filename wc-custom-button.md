//Really, nice clean code to add a custom button in WooCommerce//

<?php
/*
Plugin Name: WC Custom Button - Custom Action
Plugin URI: https://gist.github.com/maxsherlock/
Description: A simple plugin to add a custom button to WooCommerce tools
Author: Max Sommers
Contributors: maxsherlock
Author URI: https://gist.github.com/maxsherlock/
Version: 1.0
/*
/**
 * WC_Tools_Custom_Button class.
 */
class WC_Tools_Custom_Button {
	
	/**
	 * __construct function.
	 *
	 * @access public
	 * @return void
	 */
	function __construct() {
		
		add_filter( 'woocommerce_debug_tools', array( $this,'debug_button' ) );
	}
	
	/**
	 * debug_button function.
	 *
	 * @access public
	 * @param mixed $old
	 * @return void
	 */
	function debug_button( $old ) {
		$new = array(
			'my_custom_button' => array(
				'name'		=> __( 'The custom button', '' ),
				'button'	=> __( 'Click here!', '' ),
				'desc'		=> __( 'Put your custom button description here', '' ),
				'callback'	=> array( $this, 'debug_button_action' ),
			),
		);
		$tools = array_merge( $old, $new );
		
		return $tools;
	}
	
	/**
	 * debug_button_action function.
	 *
	 * @access public
	 * @return void
	 */
	function debug_button_action() {
		// do what you want here
		echo '<div class="updated"><p>' . __( 'The final custom action effect!', '' ) . '</p></div>';
	}
	
}
$GLOBALS['WC_Tools_Custom_Button'] = new WC_Tools_Custom_Button();

===

Soem background on how I created this custom button plugin and an example:

 - [Creating Custom Hooks](https://developer.wordpress.org/plugins/hooks/creating-custom-hooks/)
 - [Todd and Clare](https://www.toddandclare.com) {Search page custom button plugin I submitted on [Dating Search Page](https://www.toddandclare.com/search/)}
