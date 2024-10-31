=== SesPress ===

Contributors: coloredcow, rathorevaibhav
Plugin Name: SesPress
Plugin URI: https://coloredcow.com/wordpress
Tags: ses, aws, sespress
Author URI: https://www.coloredcow.com/
Author: ColoredCow
Requires at least: 4.7
Tested up to: 4.9.1
Requires PHP: 5.6
Stable tag: 0.1
Version: 0.1
License:           GPLv3 or later
License URI:       http://www.gnu.org/licenses/gpl-3.0.html

== Description ==

SesPress allows you to send emails using Amazon's Simple Email Service.

Major features in SesPress includes:

* Support to enable/disable the mail functionality
* Ability to add a default sender
* Test mode to override recipients with a test mode recipient at the time of testing
* Ability to send mail templates with dynamic data

== Installation ==

1) Upload the plugin files to the `/wp-content/plugins/sespress` directory, or install the plugin through the WordPress plugins screen directly.
2) Activate the plugin through the 'Plugins' screen in WordPress.
3) Use the `Settings->SesPress` screen to configure your the AWS credentials.
4) Use the following snippet in your code to use the functionality.

`add_action( 'wp', 'sespress_send_sample' );
function sespress_send_sample() {
    $args = array(
        'subject' => 'Welcome to SesPress',
        'recipients' => array(
            array(
                'name' => 'John Doe',
                'email' => 'johndoe@example.com',
            ),
            array(
                'name' => 'Jane Doe',
                'email' => 'janedoe@example.com',
            ),
        ),
        'sender' => array(
            'name' => 'Admin',
            'email' => 'admin@mysite.com',
        ),
        'message' => array(
            'html' => '<h2>Test message embedded in HTML tags.</h2>'
        ),
    );
    $sespress = new SesPress;
    $result = $sespress->send( $args );
    echo $result['data'];
}`
