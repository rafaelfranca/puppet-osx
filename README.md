# OSX Defaults Module for Puppet

Provides classes for setting various defaults in Mac OS X. Also provides a means
to set a "recovery message" to be displayed on the login and lock screens.

## Recovery Message Usage

Displays the given message on the lock and login screens.

```puppet
osx::recovery_message { 'If this Mac is found, please call 123-456-7890': }
```

## One-Shot Settings

Just `include` any of these in your manifest.

### Global Settings

* `osx::global::disable_key_press_and_hold` - disable press-and-hold for
  accented character entry
* `osx::global::enable_keyboard_control_access` - enables the keyboard for
  navigating controls in dialogs
* `osx::global::expand_print_dialog` - expand the print dialog by default
* `osx::global::expand_save_dialog` - expand the save dialog by default

### Dock Settings

* `osx::dock::2d` - use the old flat dock style
* `osx::dock::autohide` - automatically hide the tock
* `osx::dock::clear_dock` - ensures the dock only contains apps that are running
* `osx::dock::dim_hidden_apps` - dims icons of hidden apps
* `osx::dock::hide_indicator_lights` - remove the indicator lights below running
  apps

### Finder Settings

* `osx::finder::show_external_drives_on_desktop`
* `osx::finder::show_hard_drives_on_desktop`
* `osx::finder::show_mounted_servers_on_desktop`
* `osx::finder::show_removable_media_on_desktop`
* `osx::finder::show_all_on_desktop` - does all of the above
* `osx::finder::empty_trash_securely` - enable Secure Empty Trash
* `osx::finder::unhide_library` - unsets the hidden flag on ~/Library

### Universal Access Settings

* `osx::universal_access::ctrl_mod_zoom` - enables zoom by scrolling while
  holding Control
* `osx::universal_access::enable_scrollwheel_zoom` - enables zoom using the
  scroll wheel

### Miscellaneous Settings

* `osx::disable_app_quarantine` - disable the downloaded app quarantine
* `osx::no_network_dsstores` - disable creation of .DS_Store files on network
  shares

## Customizable Settings

These settings can be used like one-shots or customized.

`osx::global::key_repeat_delay` - the amount of time (in ms) before a key starts
  repeating

```puppet
include osx::global::key_repeat_delay

class { 'osx::global::key_repeat_delay':
  delay => 35
}
```

`osx::global::key_repeat_rate` - the amount of time (in ms) before key repeat
  'presses'

```puppet
include osx::global::key_repeat_rate

class { 'osx::global::key_repeat_rate':
  rate => 0
}
```

`osx::universal_access::cursor_size` - the amount the cursor will be zoomed

```puppet
include osx::universal_access::cursor_size

class { 'osx::universal_access::cursor_size':
  zoom => 1.5
}
```


## Required Puppet Modules

* boxen
* property_list_key

## Developing

Write code.

Run `script/cibuild`.
