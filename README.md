# php-study
This is for PHP learning, include Laraval framework

# Windows上使用Vagrant打造Laravel Homestead可协同跨平台开发环境

## 前言
大家对VMware或者VirtualBox一定不会陌生，虚拟化的好处自然深入人心，而现在我们可以通过Vagrant搭建一套类似Laravel Homestead完整开发环境，这样极大的减少了架设开发环境的时间，同时还支持在Windows/Mac/Linux不同平台上分享定制包，统一团队之间的开发环境提高工作效率，而Docker的出现也让未来更值得期待。
用Vagrant为自己打造一个奇妙的跨平台开发环境


阅读原文 - http://wsgzao.github.io/post/vagrant/

## 扩展阅读

> Vagrant - https://www.vagrantup.com/
> Laravel Homestead - http://laravel.com/docs/5.1/homestead
> 在windows下进行linux开发：利用Vagrant+virtualbox - http://blog.star7th.com/2015/06/1538.html
> 在 Mac/win7 下上使用 Vagrant 打造本地开发环境 - http://segmentfault.com/a/1190000002645737

## 环境准备
> Git（非必需）
> PHP（非必需）
> Laravel（非必需）
> Composer（非必需）
> Vagrant
> VirtualBox
如果大家有需要离线安装欢迎直接留言回复哈

## 安装git
1.下载GitHub for Windows

https://windows.github.com/

## 安装php
建议大家尽量安装当前最新版本的 PHP

1.下载PHP

http://windows.php.net/download/

2.解压目录

我的路径D:php

3.添加环境变量

右键计算机->高级系统设置->环境变量->系统变量->PATH

C:ProgramDataOracleJavajavapath;%SystemRoot%system32;%SystemRoot%;%SystemRoot%System32Wbem;%SYSTEMROOT%System32WindowsPowerShellv1.0;C:nodejs;D:php;C:ProgramDataComposerSetupbin

4.设置php.ini

进入 PHP 安装目录（例如 D:php）。找到 php.ini-development 文件并复制一份到当前目录，重命名为 php.ini，修改以下配置
去掉extension=php_mbstring.dll 前面的分号（888 行左右）
去掉extension=php_openssl.dll前面的分号（893 行左右）
去掉extension_dir = "ext"前面的分号（736 行左右）

5.使环境变量生效

重启explorer.exe 

## 安装Laravel
1.下载Laravel

http://www.golaravel.com/download/

2.解压目录

我的路径D:laravel-v5.1.4

3.启动Laravel

d:cd laravel-v5.1.4D:laravel-v5.1.4>php artisan serveLaravel development server started on http://localhost:8000/
在浏览器中访问http://localhost:8000/

artisan 的 serve 命令还支持两个参数：

host 设置主机地址
port 设置 web server 监听的端口号
例如：php artisan serve --port=8888

## 安装Composer
1. 下载Composer-Setup.exe

https://getcomposer.org/doc/00-intro.md#installation-windows

2.配置Composer

Loading composer repositories with package informationInstalling dependencies (including require-dev)SSL certificate problem, verify that the CA cert is OK. Details: error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed”
如果安装过程提示报错为缺少CA证书，下载cacert.pem到自定义路径
http://curl.haxx.se/docs/caextract.html

然后修改php.ini文件（1983行左右）

openssl.cafile=D:phpverifycacert.pem

3.测试Composer

composer -VComposer version 1.0-dev (d79427f1a7b15e8f4d46ce8124a4d0c58ba1479c) 2015-07-04 11:22:58
## 安装Vagrant
1.下载Vagrant

https://www.vagrantup.com/downloads.html

2.离线下载虚拟镜像

https://github.com/tommy-muehle/puppet-vagrant-boxes/releases/download/1.0.0/centos-6.6-x86_64.box

上面给出的是centos-6.6镜像下载链接，要下载其他镜像请访问官网
http://www.vagrantbox.es/

## 安装VirtualBox
BIOS里面开启CPU硬件虚拟化支持VT(Virtualization Technology)

1.下载VirtualBox

https://www.virtualbox.org/wiki/Downloads

2.导入镜像

设置VirtualBox目录并拷贝镜像centos-6.6-x86_64.box
E:VirtualBoxcentos-6.6-x86_64.box

3.命令初始化Vagrant

# 切换VirtualBox目录e:cd .VirtualBox#输入命令初始化E:VirtualBox> vagrant init centos6.6A `Vagrantfile` has been placed in this directory. You are nowready to `vagrant up` your first virtual environment! Please readthe comments in the Vagrantfile as well as documentation on`vagrantup.com` for more information on using Vagrant.#执行添加命令E:VirtualBox> vagrant box add centos6.6 centos-6.6-x86_64.box==> box: Adding box 'centos6.6' (v0) for provider:    box: Downloading: file://E:/VirtualBox/centos-6.6-x86_64.box    box: Progress: 100% (Rate: 670M/s, Estimated time remaining: --:--:--)==> box: Successfully added box 'centos6.6' (v0) for 'virtualbox'!#检查是否导入成功E:VirtualBox> vagrant box listcentos6.6 (virtualbox, 0)
Vagrant配置
详细配置文档可以参考官方手册 - https://docs.vagrantup.com/v2/

启动Vagrant
通过Shell进入目录E:VirtualBox后执行命令

 vagrant up
顺利启动的完整过程如下所示

E:VirtualBox>vagrant upBringing machine 'default' up with 'virtualbox' provider...==> default: Importing base box 'centos6.6'...==> default: Matching MAC address for NAT networking...==> default: Setting the name of the VM: VirtualBox_default_1437213832296_68434==> default: Clearing any previously set forwarded ports...==> default: Clearing any previously set network interfaces...==> default: Preparing network interfaces based on configuration...    default: Adapter 1: nat==> default: Forwarding ports...    default: 22 => 2222 (adapter 1)==> default: Booting VM...==> default: Waiting for machine to boot. This may take a few minutes...    default: SSH address: 127.0.0.1:2222    default: SSH username: vagrant    default: SSH auth method: private key    default: Warning: Connection timeout. Retrying...    default:    default: Vagrant insecure key detected. Vagrant will automatically replace    default: this with a newly generated keypair for better security.    default:    default: Inserting generated public key within guest...    default: Removing insecure key from the guest if it's present... default: Key inserted! Disconnecting and reconnecting using new SSH key... ==> default: Machine booted and ready! ==> default: Checking for guest additions in VM... default: The guest additions on this VM do not match the installed version of default: VirtualBox! In most cases this is fine, but in rare cases it can default: prevent things such as shared folders from working properly. If you see default: shared folder errors, please make sure the guest additions within the default: virtual machine match the version of VirtualBox you have installed on default: your host and reload your VM. default: default: Guest Additions Version: 4.3.28 default: VirtualBox Version: 5.0 ==> default: Mounting shared folders... default: /vagrant => E:/VirtualBox
虚拟机启动之后则可以通过 vagrant ssh 联入虚拟机进行进一步的环境配置，或者软件安装相关的工作，在Windows系统下，并不能直接通过vagrant ssh连到虚拟机，需要使用SecureCRT/Putty/Xshell等第三方工具进行连接。连接地址127.0.0.1，端口2222。登录的帐号root的密码为vagrant

E:VirtualBox> vagrant upBringing machine 'default' up with 'virtualbox' provider...==> default: Clearing any previously set forwarded ports...==> default: Clearing any previously set network interfaces...==> default: Preparing network interfaces based on configuration...    default: Adapter 1: nat    default: Adapter 2: bridged==> default: Forwarding ports...    default: 80 => 8080 (adapter 1)    default: 22 => 2222 (adapter 1)==> default: Booting VM...==> default: Waiting for machine to boot. This may take a few minutes...The guest machine entered an invalid state while waiting for itto boot. Valid states are 'starting, running'. The machine is in the'poweroff' state. Please verify everything is configuredproperly and try again.If the provider you're using has a GUI that comes with it, it is often helpful to open that and watch the machine, since the GUI often has more helpful error messages than Vagrant can retrieve. For example, if you're using VirtualBox, run `vagrant up` while theVirtualBox GUI is open.
如果有报上述错误，并且运行Virtualbox去安装系统时出错：Failed to open a session for the virtual machine，Unable to load R3 module C:Program FilesOracleVirtualBox/VBoxDD.DLL (VBoxDD): GetLastError=1790 (VERR_UNRESOLVED_ERROR).，需要使用UniversalThemePatcher还原未破解的themeservice.dll themeui.dll uxtheme.dll文件

已经打包好的下载链接 - http://pan.baidu.com/s/1c0HGj2g

==> default: Booting VM...==> default: Waiting for machine to boot. This may take a few minutes...    default: SSH address: 127.0.0.1:2222    default: SSH username: vagrant    default: SSH auth method: private key    default: Warning: Connection timeout. Retrying...    default: Warning: Connection timeout. Retrying...    default: Warning: Connection timeout. Retrying...
如果报default: Warning: Connection timeout. Retrying...，建议打编辑Vagrantfile打开VirtualBox图形化界面vb.gui = true进一步分析错误代码和原因。

导出box
通过Shell进入目录E:VirtualBox后执行命令

vagrant packagevagrant package --output NAME --vagrantfile FILE#可选参数：--output NAME ： （可选）设置通过NAME来指定输出的文件名--vagrantfile FILE：（可选）可以将Vagrantfile直接封进box中
完成后会在当前目录就会生成package.box，可以在家或者团队成员共享开发环境保持一致性

其它命令
vagrant up （启动虚拟机）
vagrant halt （关闭虚拟机??对应就是关机）
vagrant suspend （暂停虚拟机??只是暂停，虚拟机内存等信息将以状态文件的方式保存在本地，可以执行恢复操作后继续使用）
vagrant resume （恢复虚拟机 ?? 与前面的暂停相对应）
vagrant box remove centos6.6 （移除box，其中centos6.6是box名）
vagrant destroy （删除虚拟机，删除后在当前虚拟机所做进行的除开Vagrantfile中的配置都不会保留）

## Laravel Homestead
细节部分可参考官方文档 - http://laravel.com/docs/5.1/homestead

1.下载安装包

vagrant box add laravel/homesteadE:Homestead>vagrant box add laravel/homestead==> box: Loading metadata for box 'laravel/homestead'    box: URL: https://atlas.hashicorp.com/laravel/homesteadThis box can work with multiple providers! The providers that itcan work with are listed below. Please review the list and choosethe provider you will be working with.1) virtualbox2) vmware_desktopEnter your choice: 1==> box: Adding box 'laravel/homestead' (v0.2.7) for provider: virtualbox    box: Downloading: https://vagrantcloud.com/laravel/boxes/homestead/versions/0.2.7/providers/virtualbox.box    box: Progress: 0% (Rate: 9d/s, Estimated time remaining: 0:05:30)11))
由于国内网络环境问题建议离线下载后手动导入

#输入命令初始化E:Homestead>vagrant init laravelA `Vagrantfile` has been placed in this directory. You are nowready to `vagrant up` your first virtual environment! Please readthe comments in the Vagrantfile as well as documentation on`vagrantup.com` for more information on using Vagrant.#执行添加命令E:Homestead>vagrant box add laravel laravel.box==> box: Box file was not detected as metadata. Adding it directly...==> box: Adding box 'laravel' (v0) for provider:    box: Unpacking necessary files from: file://E:/Homestead/laravel.box    box: Progress: 100% (Rate: 141M/s, Estimated time remaining: --:--:--)==> box: Successfully added box 'laravel' (v0) for 'virtualbox'!#检查是否导入成功E:Homestead>vagrant box listcentos6.6 (virtualbox, 0)laravel   (virtualbox, 0)#启动Lavarel HomesteadE:Homestead>vagrant upBringing machine 'default' up with 'virtualbox' provider...==> default: Importing base box 'laravel'...==> default: Matching MAC address for NAT networking...==> default: Setting the name of the VM: Homestead_default_1437217549272_56101==> default: Clearing any previously set network interfaces...==> default: Preparing network interfaces based on configuration...    default: Adapter 1: nat==> default: Forwarding ports...    default: 22 => 2222 (adapter 1)==> default: Booting VM...==> default: Waiting for machine to boot. This may take a few minutes...    default: SSH address: 127.0.0.1:2222    default: SSH username: vagrant    default: SSH auth method: private key    default: Warning: Connection timeout. Retrying...    default:    default: Vagrant insecure key detected. Vagrant will automatically replace    default: this with a newly generated keypair for better security.    default:    default: Inserting generated public key within guest...    default: Removing insecure key from the guest if it's present... default: Key inserted! Disconnecting and reconnecting using new SSH key... ==> default: Machine booted and ready! ==> default: Checking for guest additions in VM... default: The guest additions on this VM do not match the installed version of default: VirtualBox! In most cases this is fine, but in rare cases it can default: prevent things such as shared folders from working properly. If you see default: shared folder errors, please make sure the guest additions within the default: virtual machine match the version of VirtualBox you have installed on default: your host and reload your VM. default: default: Guest Additions Version: 4.3.14 default: VirtualBox Version: 5.0 ==> default: Mounting shared folders... default: /vagrant => E:/Homestead
登录帐户vagrant/vagrant，开始全新的Laravel Homestead体验之旅吧。
