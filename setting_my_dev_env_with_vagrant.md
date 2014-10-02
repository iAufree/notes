# ruby on rails 环境搭建

8.  安装vagrant,virtualbox,SecureCRTP;
8.  安装vagrant和virtualBox;
8.  建立并进入开发环境目录;
8.  [下载](http://www.vagrantbox.es/)box;
8.  添加box`vagrant box add base ` + 远端的box地址或者本地的box文件名,先下载到本地再添加速度会比较快;
8.  vagrant init;
8.  vagrant up  # 启动环境,改写vagrantfile里面的`config.    vm.network :forwarded_port, guest: 3000, host: 3000`以及vagrant的ID信息;
8.  打开SecureCRTPortable # 主机名为127.0.0.1,填写端口,账户密码等相关信息;
8.  Install Git with Apt-Get command:sudo apt-get install git-core;
8.  sudo apt-get update;
8.  使用cmd 到D:develoment/Freetalks/ 运行  vagrant reload(重启);
8.  重新连接SecureCrt;
8.  跟着教材安装其它东西
8.  http://mirrors.163.com/.help/ubuntu.html;
8.  请加sudo编辑`sources.list`
8.  安装rails时使用 RubyGems 镜像;
8.  创建一个新项目 rails new XX;
8.  bundle install处按ctrl+C退出,修改gemfile里面的文件为sources: http://ruby.taobao.org
8.  cd your_project_name , rails server;
8.  网站查看: localhost:3032;
8.  done;

which ruby,查看ruby path.



#note add

1.git init;(初始化一个仓库)
2. git add .;(将所以文件全部加入跟踪列表)

##note modify

3. git commit -am "write something"(提交到仓库)
4. git push;(将所以内容推送到github)
5. git status;(查看git哪处发生改动)

##其他
`*git checkout -b branchname;`(新建并且切换到branchname)

`*git branch;`(查看所有分支,前面带*的为当前分支)

`*git checkout master;`(切换到主分支)

`*git merge branchname;`(合并branchname到主分支,切记:合并分支前得先切换到master)

 markedown
 http://mirrors.163.com/.help/ubuntu.html



关于github无法加载CSS,js的解决方法:

修改hosts文件，直接通过IP访问github的CDN fastly.net，不用域名解析。

通过 www.ipaddress.com  这个网站,点击Reverse IP查询github.global.ssl.fastly.net的IP地址，进入C:\Windows\System32\etc,在hosts里面加上

	#fix github cdn problem because of GFW
	185.31.17.184  github.global.ssl.fastly.net


获取key
key  cat ~/.ssh/id_rsa.pub

ST2:ctrl+K+B,神shortcuts也~

设置gem sources方法:


`$ gem sources --remove https://rubygems.org/` #移除原来的sources<br/>
`$ gem sources -a http://ruby.taobao.org/` #添加taobao的sources<br/>
`$ gem sources -l` #查看gem sources的列表<br/>

部署到heroku时无法查看layout的
[解决方法](http://stackoverflow.com/questions/12719541/css-loading-locally-but-not-in-heroku-for-a-rails-app),个人推荐:

	Run bundle exec rake assets:precompile on your local code

	Commit the changes and deploy to heroku

如果程序加入了字体,在运行`assets:precomple`后,若在生产环境没有字体没有被编译,在`application.rb`里面加入:

	
    config.assets.paths << Rails.root.join("app", "assets", "fonts")
    config.assets.precompile += %w(.svg .eot .woff .ttf )

试着在这一命令行中加入`RAILS_ENV=production`运行.

本地git仓库出错,解决方法,可以重新从github上面的仓库clone下来,然后使用

	git remote add heroku git@heroku.com:{appname}.git

远程添加heroku原来部署的应用,如果出现卡在`writing objects`的情况,可以尝试将git重新打包

	git repack
	git push

新建git分支后,若要删除分支的所有内容,必须得先`add`及`commit -m`分支中的内容,再使用`git branch -D {branch-name}`将其删除.注意,应该使用`D`,而不是`d`.


git push heroku时若出现

	Warning: Permanently added the RSA host key for IP address '50.19.85.132' to the list of known hosts.
	Permission denied (publickey).
	fatal: The remote end hung up unexpectedly

可以尝试这种[方法](http://stackoverflow.com/questions/7305673/git-clone-fails-for-heroku-project):

	$ssh-keygen -t rsa
	$heroku keys:clear
	$heroku keys:add 
	$git clone git@heroku.com:my-app.git -o heroku

我没有加最后一步,但还是成功了.


#关于sublime.
 按下Ctrl+Shift+P调出命令面板
 输入install 调出 Install Package 选项并回车，然后在列表中选中要安装的插件。
 see also:[sublime插件](http://www.qianduan.net/essential-to-sublime-the-text-2-plugins.html)

