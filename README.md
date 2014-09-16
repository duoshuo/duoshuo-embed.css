## embed.css

embed.css 项目是多说评论框 CSS 样式源代码

### 开发环境指南

首先，确保你的开发环境中安装了 Node.js，然后通过 `$ npm install` 来安装项目开发依赖

```bash
$ git clone git@github.com:duoshuo/duoshuo-embed.css.git
$ cd duoshuo-embed.css
$ npm install
```

开启实时调试与编译工具
```bash
$ npm run dev
```

此工具会监听 `less` 目录下文件变动，并编译最新的 `dist/*.css` 文件。

### 安装与使用自定义样式方法

#### 手动修改

1.在你的网页中的 `duoshuoQuery` 部分找到：

```js
var duoshuoQuery = {short_name : 'XXXX'};
```

2.增加 theme : 'none'

```js
var duoshuoQuery = {short_name : 'XXXX', theme : 'none'};
```

这样，多说就不会加载自己的样式。  

#### WordPress 插件

WordPress 插件中, 请找到 `WordPress.php`, 搜索 `duoshuoQuery`

**注意**: 一共要调整两处

```php
var duoshuoQuery = <?php echo json_encode($this->buildQuery());?>;
```
    
在此行后加上:

```js
duoshuoQuery.theme = 'none';
```

3.加载自定义的 embed.css，需要在 `<head></head>` 中加入

```html
<link rel="stylesheet" type="text/css" href="{路径}embed.css" />
```

### 开发建议

建议通过修改 `variables.less` 来自定义配色

建议将对特定样式的修改都写在 `custom.less` 中

由于官方的代码经常更新，建议经常merge 官方代码。

```bash
$ git fetch origin
$ git merge origin master 
```

### 主题发布方法

1. 在github上fork这个duoshuo-embed.css项目
2. git clone 到本地
3. 以你主题的名字，创建一个branch(分支)，并切换到这个分支上
4. 开发代码(小幅修改建议写在custom.less中)
5. `$ git push`，在[多说开发者中心](http://dev.duoshuo.com/)发帖，或者发信给多说团队

### 样式参考

- [多说开发者中心的CSS开发指南](http://dev.duoshuo.com/docs/4ff1cfd0397309552c000017)

### 联系方式
如果你想分享自己的主题设计，请邮件联系：zhenyu@duoshuo.com，或者到[多说开发者中心](http://dev.duoshuo.com/)发帖。
