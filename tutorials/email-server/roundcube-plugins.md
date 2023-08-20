# 🔌 Roundcube plugins

View the Craft version [here](https://www.craft.me/s/QaXmAaCow3iS7o) (latest)

Readme version (might be outdated):

Install `composer`

```other
cd /var/www/roundcube
curl -s https://getcomposer.org/installer | php

cp composer.json-dist composer.json
```

[Browse](https://packagist.org/?type=roundcube-plugin) through the repository and find the plugins you want to install.

To add plugins

```php
php composer.phar require "package-name"
```

To install plugins

```php
php composer.phar install
```

To update plugins

```php
php composer.phar update
```

Recommended plugins to enable:

```php
$config['plugins'] = [
	'acl',
	'additional_message_headers',
	'archive',
	'attachment_reminder',
	'autologon',
	'debug_logger',
	'emoticons',
	'enigma',
	'filesystem_attachments',
	'help',
	'hide_blockquote',
	'http_authentication',
	'identicon',
	'identity_select',
	'jqueryui',
	'krb_authentication',
	'managesieve',
	'markasjunk',
	'new_user_dialog',
	'new_user_identity',
	'newmail_notifier',
	'password',
	'reconnect',
	'show_additional_headers',
	'squirrelmail_usercopy',
	'subscriptions_option',
	'userinfo',
	'vcard_attachments',
	'virtuser_file',
	'virtuser_query',
	'zipdownload',
	'kolab_2fa',
	'twofactor_webauthn',
	'contextmenu',
	'swipe',
	'calendar',
	'authres_status',
	'libkolab',
	'libcalendaring',
	'advanced_search',
];
```

The plugins `kolab_2fa` and `otphp` are broken, download the files below for the patch:

[![plugins.zip](plugins.zip)](https://res.craft.do/user/full/0f469d42-b538-0763-d270-25c77bccde74/doc/5B8FCAC1-8197-4A00-90C7-16C6290AB26E/A6E6B348-8509-44F0-BCE2-396B762BDB65_2/EaqspPv1L2yqfP0ixjuQrZ6uBmCGIE9DFUyBMi0cd3oz/plugins.zip)

[![vendor.zip](vendor.zip)](https://res.craft.do/user/full/0f469d42-b538-0763-d270-25c77bccde74/doc/5B8FCAC1-8197-4A00-90C7-16C6290AB26E/0FC932D0-41BB-4476-82D2-A98FEBB38C86_2/NzD4PKhlGBPPGzQeZGGJXhzK8lLBMtAlPWdyashTQVoz/vendor.zip)

If the above patch no longer works, debug with:

```php
tail -f /var/www/roundcube/logs/errors.log
```
