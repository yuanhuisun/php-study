```
Composer 是 PHP 的一个依赖管理工具。它允许你申明项目所依赖的代码库，它会在你的项目中为你安装他们。
------- Composer官方定义
```
Composer给PHP开发带来了极大的便利，如果你的项目想引用别人发布的包，那么直接comoposer install即可，composer可安装的项目相当的丰富，凡是能从https://github.com上搜索到的并且发布到https://packagist.org网站的带有composer.json文件PHP项目，都可以执行安装。我们一直install别人写的程序包，如果自己也写一个程序包，然后自己可以composer install，并且别人也可以comopser install是一件很酷的事。那么我们应当怎么做呢？

# 准备工作：

首先你的电脑需要安装composer，并学会如何熟练使用它的各种命令（请参考资料 https://docs.phpcomposer.com进行学习安装）
在https://github.com上申请一个账号（如果已有，可以略过）
在https://packagist.org上申请一个账号（也可以用github账号登陆）
本地需要有php环境（这一句是废话）
如果以上三步工作你都具备了的话，那么恭喜你，万事俱备，只欠东风！我们可以开始进入正题了。

# 一. 创建github项目helloword
image

点击“create repository”按钮，即可以创建成功（注意，勾选一下Initialize this repository with a README选项，可以在创建项目的时候初始化一个文件）。
image
创建成功之后，可以去项目主页看下效果。

# 二. 编写composer.json文件
我们已经创建了一个全新的空项目，但是这个时候，我们直接去composer install 是安装不上的，因为composer根本找不到你的项目。想让composer能找到你的项目，需要两个必要的条件，需要给项目建立一个composer可识别的name，并且需要发布项目。

新建一个composer.json的文件，文件内容如下：
```
{
  "name":"rockyfc/helloworld"
}
```
注意：这个name就是本项目的唯一识别key，composer会根据此name查找项目。

将项目发布到https://packagist.org网站（发布地址是https://packagist.org/packages/submit），整个发布过程很简单，此处不再赘述。

# 三. 本地用composer 安装helloworld项目

以上我们讲了如何一步一步建立并发布自己composer项目，如果你按照步骤操作完成了，那么恭喜你，你已经成功创建了一个最简单的composer项目，那接下来，我们在本地安装一下试试我们的安装包是否可用。

为了方便查看效果，我们在本地新创建一个空文件夹（假设本地文件夹目录是“/github/helloworld”），新建composer.json文件，内容如下：
```
{
  "repositories": {
     "packagist": {
       "type": "composer",
       "url": "https://packagist.org"
     }
   }
}
```
命令行模式下执行如下命令安装：
```
composer require rockyfc/helloworld dev-master
```
注意：dev-master表示当前的开发版本，在没有发布正式版本之前，请使用此固定写法。

待程序执行完成之后，看下“/github/helloworld”的目录结构，
```
├── composer.json
├── composer.lock
└── vendor
    ├── autoload.php
    ├── composer
    │   ├── ClassLoader.php
    │   ├── LICENSE
    │   ├── autoload_classmap.php
    │   ├── autoload_namespaces.php
    │   ├── autoload_psr4.php
    │   ├── autoload_real.php
    │   ├── autoload_static.php
    │   └── installed.json
    └── rockyfc
        └── helloworld
            ├── README.md
            └── composer.json
```
composer在当前目录下生成了一个vendor文件夹，里面就有刚才我们自己编写的helloworld项目。

到此为止，我们已经成功的创建并发布了一个最简单的项目，并且在本地成功安装。但是有的小伙伴会问了，我怎么去向包里面添加php程序呢？别急，我们在下一个章节会讲到。

作者：softfc
链接：https://www.jianshu.com/p/945993a7bf2a
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
