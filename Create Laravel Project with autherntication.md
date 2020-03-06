# 创建自己的Laravel项目

## 创建一个新的Laravel项目
首先到自己的代码开发的目录，比如`C:\\Code`, 然后使用composer创建laravel项目
```
user@mylaptop MINGW64 /c/code
composer create-project laravel/laravel myproject
```

这样，一个全新的laravel项目就在`//c//code`下建好了。  

## 安装laravel ui
```
composer require laravel/ui
```

## 配置vue和授权管理
```
php artisan ui vue --auth
```

这样，一个全新laravel项目就建立好了，并且具备了简单的授权管理。
