=== Social Media Shortcode Pack ===
Contributors: tw2113
Tags: social media, shortcodes
Requires at least: 3.7
Tested up to: 3.9.1
Stable tag: 1.1
License: WTFPL
License URI: http://sam.zoy.org/wtfpl/

Registers shortcodes for your posts, pages, or post types that display user profile links to various social media websites.

== Description ==

This plugin registers shortcodes for the following websites, social service on the left, format for the shortcode on the right:

Service / shortcode version

* Colourlovers [colourlovers]
* Delicious [delicious]
* Digg [digg]
* Dribbble [dribbble]
* Facebook [facebook]
* Favstar.FM [favstarfm]
* Flickr [flickr]
* Forrst [forrst]
* Foursquare [foursquare]
* GitHub [github]
* Last.FM [lastfm]
* LinkedIn [linkedin]
* Myspace [myspace]
* OkCupid [okcupid]
* Programmable Web [programmableweb]
* Reddit [reddit]
* Scribd [scribd]
* SlideShare [slideshare]
* StumbleUpon [stumbleupon]
* Twitter [twitter]
* Vimeo [vimeo]
* YouTube [youtube]

All examples updated for v1.1

Example 1:

`[twitter name="JoeSomeone" text="some text you want the link to appear as"]`

results in:

`<a href="http://www.twitter.com/JoeSomeone" title="JoeSomeone's Twitter profile\" class="twitter_smsc">some text you want the link to appear as</a>`

on your post/page

Example 2:

`[twitter name="JoeSomeone"]`

results in:

`<a href="http://www.twitter.com/JoeSomeone" title="JoeSomeone's Twitter profile\" class="twitter_smsc">JoeSomeone (Twitter)</a>`

on your post/page.

Example 3:

`[twitter name="JoeSomeone" target="_blank"]`

results in:

`<a href="http://www.twitter.com/JoeSomeone" title="JoeSomeone's Twitter profile\" target="_blank" class="twitter_smsc">JoeSomeone (Twitter)</a>`

on your post/page.

== Installation ==

1. Search for "Social Media Shortcodes" via your WP Admin plugin installer and activate.
1. Write some blog posts.
1. Link some social media sites profiles.
1. You look very nice today, did you get your hair did?
1. Ignore what Grumpy Cat thinks of your post. It's wonderful.

== Frequently Asked Questions ==

### How to use the provided filters

`
function example_add_site( $sites ) {
	/*
	$sites is going to be an array of arrays.
	"somesite" should be the word you want to use with the shortcode
	"Some Site" is the "pretty" name for the site
	"http://www.somesite.com/user/" is the url for a user's profile, without the user name appended
	 */
	$sites['somesite'] = array( 'Some Site', 'http://www.somesite.com/user/' );

	//Return the $sites array
	return $sites;
}
add_filter( 'smsc_shortcodes', 'example_add_site' );

function example_add_classes( $classes ) {
	/*
	$classes will be an array
	 */

	$classes[] = 'someclass';

	/*
	class attribute that be added to the <a> tag will be: class="smsc somesite_smsc someclass"
	 */
	return $classes;
}
add_filter( 'smsc_classes', 'example_add_classes' );

function example_change_final_link( $output, $shortcode ) {
	/*
	$output will be the final constructed link that will be displayed in your post
	$shortcode is the shortcode word used for the current shortcode. Example: "somesite". Useful for conditional application.
	 */

	if ( 'somesite' == $shortcode ) {
		$output_new = $output . ' <--Awesome profile!';
	}

	/*
	$output_new will equal:
	"<a href="http://www.somesite.com/user/tw2113" title="tw2113's Some Site profile" class="smsc somesite_smsc" target="_blank">test text</a> <--Awesome profile!"
	*/

	return $output_new;
}
add_filter( 'smsc_final_link', 'example_change_final_link', 10, 2 );
`

== Screenshots ==

None

== Changelog ==

= 1.1 =
* Rewrote the plugin as a PHP Class.
* Added or amended three filters for developers to use: "smsc_shortcodes", "smsc_classes", "smsc_final_link"
* Updated default site list

= 1.0.3 =
* Added classes to the link markup based on social media site. Twitter will get 'class="twitter_smsc"' and so on. Added optional target parameter to shortcode in case someone wants to open in different browser windows.

= 1.0.2 =
* Added is_array() check after filter and some function documentation.

= 1.0.1 =
* Added filter for users to add their own sites.

= 1.0 =
* Initial upload

== Upgrade Notice ==

= 1.1 =
* Rewrote the plugin as a PHP Class.
* Added or amended three filters for developers to use: "smsc_shortcodes", "smsc_classes", "smsc_final_link"
* Updated default site list

= 1.01 =
Just a new filter to add your own sites with.

= 1.0.2 =
* Added is_array() check after filter and some function documentation.

= 1.0.3 =
* Added class output for the links and optional browser window target for shortcode.
