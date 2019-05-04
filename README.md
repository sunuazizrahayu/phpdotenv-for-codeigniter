# PHP DotEnv for CodeIgniter
> Autodetect environment type and load variables from `.env` to `getenv()`, `$_ENV` and `$_SERVER` automagically.

![](cover.png)





## Installation
1. Install Composer
```
$ curl -s http://getcomposer.org/installer | php
```

2. Paste all of these files to your CodeIgniter root.
3. Install package on `application` directory
```
$ cd application
$ composer install
```





## Configuration
1. Enable your Composer Autoload and Hooks: `application/config/config.php`

`$config['enable_hooks'] = FALSE;` to `$config['enable_hooks'] = TRUE;`

`$config['composer_autoload'] = FALSE;` to `$config['composer_autoload'] = TRUE;`


2. Add this code to your application hooks: `application/config/hooks.php`

```
// Use this code if your .env files on *CodeIgniter ROOT* folder
$hook['pre_system'] = function() {
	$dotenv = Dotenv\Dotenv::create(FCPATH);
	$dotenv->load();
};
```

or
```
// Use this code if your .env files on *application* folder
$hook['pre_system'] = function() {
	$dotenv = Dotenv\Dotenv::create(APPPATH);
	$dotenv->load();
};
```

3. Create your *.env* files
```
$ cp .env.example .env
```





## Usage Example

### Database Configuration
1. Edit `database.php` on `application/config/database.php`
2. Replace this code:
```
	'hostname' => 'localhost',
	'username' => '',
	'password' => '',
	'database' => '',
	'dbdriver' => 'mysqli',
```

to
```
	'hostname' => getenv('DB_HOSTNAME'),
	'username' => getenv('DB_USERNAME'),
	'password' => getenv('DB_PASSWORD'),
	'database' => getenv('DB_DATABASE'),
	'dbdriver' => getenv('DB_DRIVER'),
```






## Contributing
1. Fork it!
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Make your changes
4. Commit your changes (`git commit -am 'Add my feature'`)
5. Push to the branch (`git push origin my-new-feature`)
6. Create a new Pull Request
