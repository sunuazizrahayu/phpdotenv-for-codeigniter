# PHP DotEnv for CodeIgniter
> Autodetect environment type and load variables from `.env` to `getenv()` or `$_ENV` automagically.

![](cover.png)


## Installation
1. Paste all of these files to your CodeIgniter Application root.
2. Add `.env` on your `.gitignore` on CodeIgniter root.
3. Enable your Composer Autoload and Hooks on `application/config/config.php`

`$config['composer_autoload'] = FALSE;` to `$config['composer_autoload'] = TRUE;`

`$config['enable_hooks'] = FALSE;` to `$config['enable_hooks'] = TRUE;`

4. Go to your `application` directory and install package.
```
cd application && composer install
```

5. Add this script to your application hooks on `application/config/hooks.php`
```
$hook['pre_system'] = function() {
	$dotenv = Dotenv\Dotenv::create(FCPATH);
	$dotenv->load();
};
```


## Contributing

1. Fork it!
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Make your changes
4. Commit your changes (`git commit -am 'Add my feature'`)
5. Push to the branch (`git push origin my-new-feature`)
6. Create a new Pull Request
