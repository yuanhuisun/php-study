# 使用composer创建项目

## 使用composer初始化一个新项目
···
yuanhui.sun@DLC040186284953 MINGW64 /c/code/x-space
$ composer init

  Welcome to the Composer config generator

This command will guide you through creating your composer.json config.
···
按提示依次输入package name（默认为当前用户/当前目录）/package描述/作者/稳定版本/packet类型（库/项目/元包/composer的plugin）/版权
···
Package name (<vendor>/<name>) [yuanhui.sun/x-space]:
Description []: x-space is a laravel project with pre-defined CRUD role-perssion
Author [yuanhui.sun <yuanhui.sun@hotmail.com>, n to skip]:
Minimum Stability []:
Package Type (e.g. library, project, metapackage, composer-plugin) []: project
License []: MIT
····

然后定义项目的dependencies，按照提示，查找/确定项目需要的包；

····
Define your dependencies.

Would you like to define your dependencies (require) interactively [yes]? yes
Search for a package: laravel

Found 15 packages matching laravel

   [0] laravel/framework
   [1] laravel/laravel
   ... ...
   [14] barryvdh/laravel-dompdf

Enter package # to add, or the complete package name if it is not listed: 1
Enter the version constraint to require (or leave blank to use the latest version):
Using version ^6.12 for laravel/laravel
Search for a package: laravel/ui
Enter the version constraint to require (or leave blank to use the latest version):
Using version ^1.2 for laravel/ui
Search for a package: phpunit

Found 15 packages matching phpunit

   [0] phpunit/phpunit
   [1] phpunit/php-code-coverage
   ...
   [14] brianium/paratest

Enter package # to add, or the complete package name if it is not listed: 1
Enter the version constraint to require (or leave blank to use the latest version):
Using version ^8.0 for phpunit/php-code-coverage
```

选择好依赖包以后，直接在"Search for a package:"输入<kbd>Enter<kbd>

```
Would you like to define your dev dependencies (require-dev) interactively [yes]? yes
Search for a package:

{
    "name": "yuanhui.sun/x-space",
    "description": "x-space is a laravel project with pre-defined CRUD role-perssion",
    "type": "project",
    "require": {
        "laravel/laravel": "^6.12",
        "laravel/ui": "^1.2",
        "phpunit/php-code-coverage": "^8.0"
    },
    "license": "MIT",
    "authors": [
        {
            "name": "yuanhui.sun",
            "email": "yuanhui.sun@hotmail.com"
        }
    ]
}

Do you confirm generation [yes]? yes
```
让composer按照配置安装相应的关联package

```
Would you like to install dependencies now [yes]? yes
Loading composer repositories with package information
Updating dependencies (including require-dev)
Package operations: 58 installs, 0 updates, 0 removals
  - Installing symfony/polyfill-mbstring (v1.14.0): Downloading (100%)
  - Installing symfony/polyfill-php72 (v1.14.0): Downloading (100%)
  ...
  - Installing phpunit/php-file-iterator (3.0.0): Downloading (100%)
  - Installing phpunit/php-code-coverage (8.0.1): Downloading (100%)
symfony/var-dumper suggests installing ext-intl (To show region name in time zone dump)
symfony/service-contracts suggests installing symfony/service-implementation
...
ramsey/uuid suggests installing ramsey/uuid-doctrine (Allows the use of Ramsey\Uuid\Uuid as Doctrine field type.)
ramsey/uuid suggests installing paragonie/random-lib (Provides RandomLib for use with the RandomLibAdapter)
symfony/translation suggests installing symfony/config
symfony/translation suggests installing symfony/yaml
monolog/monolog suggests installing graylog2/gelf-php (Allow sending log messages to a GrayLog2 server)
monolog/monolog suggests installing doctrine/couchdb (Allow sending log messages to a CouchDB server)
...
laravel/framework suggests installing symfony/cache (Required to PSR-6 cache bridge (^4.3.4).)
laravel/framework suggests installing symfony/psr-http-message-bridge (Required to use PSR-7 bridging features (^1.2).)
laravel/framework suggests installing wildbit/swiftmailer-postmark (Required to use Postmark mail driver (^3.0).)
sebastian/environment suggests installing ext-posix (*)
phpunit/php-code-coverage suggests installing ext-pcov (*)
phpunit/php-code-coverage suggests installing ext-xdebug (*)
Writing lock file
Generating autoload files
···

这样一个新项目就建立好了
···
yuanhui.sun@DLC040186284953 MINGW64 /c/code/x-space
$ ls
composer.json  composer.lock  vendor/
···
相应的package都安装在vendor下面
···
yuanhui.sun@DLC040186284953 MINGW64 /c/code/x-space/vendor
$ ls
autoload.php  dragonmantank/  league/   paragonie/  ramsey/       tijsverkoyen/
bin/          egulias/        monolog/  phpoption/  sebastian/    vlucas/
composer/     fideloper/      nesbot/   phpunit/    swiftmailer/
dnoegel/      jakub-onderka/  nikic/    psr/        symfony/
doctrine/     laravel/        opis/     psy/        theseer/
····
