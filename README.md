# Easy WordPress Admin Notifications
A simple class that allows you to set and display WordPress admin notifications (success, notice, warning, and info messages) in the dashboard.

One frustration with the standard WordPress notification hook ([admin_notices](https://codex.wordpress.org/Plugin_API/Action_Reference/admin_notices)) is that it isn't straightforward to add a new notification after certain events have occurred. What prompted me to write this was the fact that I couldn't easily create a new admin_notice as a result of something that happened during the save_post action hook. This is because the browser refreshes after that hook fires.

This class works by storing all notices in the options table. When the admin_notices action runs, we check for any stored messages, display them, and then clear them out of the options table.

See https://codex.wordpress.org/Plugin_API/Action_Reference/admin_notices for more details.

## Requirements
PHP 5.4+ for short array syntax

## Installation

It's recommended you use this as a [must use](https://codex.wordpress.org/Must_Use_Plugins) WordPress plugin. Simply download the file and place it into your wp-content/mu-plugins directory. It should exist here:

```
/wp-content/mu-plugins/johns-admin-notices.php
```

WordPress will automatically load the file and you will then be able to use the functionality throughout your theme or plugin.

Or feel free to put this directly inside your theme or plugin and rename everything. I'm happy as long as you find it useful.

## Usage

There are 4 different functions you can use to add a notice. Here is some example usage:

```php
add_action('admin_init', function() {
    jp_notices_add_error('These messages');
    jp_notices_add_info('are really');
    jp_notices_add_success('easy to');
    jp_notices_add_warning('create');
});
```

This would result in the following output on every page load of the dashboard:

![Image showing output of above code in WordPress admin](http://imgur.com/dTDRFwX.png)

## Feedback

This is just something I created because I found it useful for a project, but I would be happy to consider any feedback.