embed.css
=========

多说评论框CSS样式源代码

## 安装方法
安装less

    sudo npm install -g less


编译embed.css

    lessc -x embed.less > embed.css


在你的网页中的duoshuoQuery部分:

    var duoshuoQuery = {short_name : 'XXXX'};


增加 theme : 'none'

    var duoshuoQuery = {short_name : 'XXXX', theme : 'none'};


这样，多说就不会加载自己的样式。  

WordPress插件中,请找到WordPress.php,搜索duoshuoQuery(注意一共要调整两处):

    var duoshuoQuery = <?php echo json_encode($this->buildQuery());?>;
    
在此行后加上:

    duoshuoQuery.theme = 'none';



你自己来加载由你自己编译的embed.css，在head中加入

    <link rel="stylesheet" type="text/css" href="{路径}embed.css" />


## 开发建议
建议通过修改variables.less来自定义配色

建议将对特定样式的修改都写在custom.less中

由于官方的代码经常更新，建议经常merge 官方代码。

    git fetch origin
    git merge origin master 


## 主题发布方法
1. 在github上fork这个duoshuo-embed.css项目
2. git clone 到本地
3. 以你主题的名字，创建一个branch(分支)，并切换到这个分支上
4. 开发代码(小幅修改建议写在custom.less中)
5. git push，在[多说开发者中心](http://dev.duoshuo.com/)发帖，或者发信给多说团队

## 样式参考
1. [多说开发者中心的CSS开发指南](http://dev.duoshuo.com/docs/4ff1cfd0397309552c000017)

## 联系方式
如果你想分享自己的主题设计，请邮件联系：zhenyu@duoshuo.com，或者到[多说开发者中心](http://dev.duoshuo.com/)发帖。
