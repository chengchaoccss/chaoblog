

---

### 心得

今天学习了利用hexo来搭建个人博客，并上传到github来实现远程访问，遇到了一些小问题，在此做一个整体记录，防止后面忘记，也为需要的同学提供一个参考。

<!--more-->

### 第一步：下载node.js和git

node.js链接：https://nodejs.org

git链接：https://git-scm.com/

### 第二步：安装hexo

```
npm install hexo-cli -g
```

### 第三步：创建博客文件夹

```
hexo init chaoBlog
或者手动创建文件夹，进入文件夹后使用命令：hexo init

进入chaoBlog文件夹，使用hexo g命令及hexo s命令便能实现本地网页浏览。
```

### 第四步：上传github

``` 
在github上创建空的仓库，仓库名必须是github用户名.github.io
其中我的github用户名是：chengchaoccss
创建好以后，修改_config.yml文件

# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repo: https://github.com/chengchaoccss/chengchaoccss.github.io.git
  branch: master
  
修改好以后使用命令：hexo d上传
```



### 第五步：更换主题

常用的主题是next

```
$ cd <博客存放的目录>
$ git clone https://github.com/iissnan/hexo-theme-next themes/next
```

下载好以后修改config.yml文件即可，**需要注意的是该主题home和archives跳转会出现404错误，所以需要对next主题里面的config文件进行修改，修改内容参照landscape主题**。

```
menu:
  home: /
  #about: /about/ || user
  #tags: /tags/ || tags
  #categories: /categories/ || th
  archives: /archives
  #schedule: /schedule/ || calendar
  #sitemap: /sitemap.xml || sitemap
  #commonweal: /404/ || heartbeat


```



### 第六步：为博文加密

参考文章：https://blog.csdn.net/wcc178399/article/details/103985916

```
1.打开themes->next->layout->_partials->head.swig文件,在以下位置插入这样一段代码


<script>
    (function(){
        if('{{ page.password }}'){
            if (prompt('请输入文章密码') !== '{{ page.password }}'){
                alert('密码错误！');
                history.back();
            }
        }
    })();
</script>

2.在需要加密的博文(title下面)前面加上密码：
password: 123456 (好像只能数字？)
```

### 第七步：hexo图片显示问题

参考文章：https://www.cnblogs.com/Jesee/p/11234387.html

```
1. 在根目录下配置文件_config.yml 中有 post_asset_folder:false改为true。这样在建立文件时，Hexo会自动建立一个与文章同名的文件夹，这样就可以把与该文章相关的所有资源（图片）都放到那个文件夹里方便后面引用。如这里我放了一张test.jpg的图片。

2. git bash安装插件：npm install https://github.com/7ym0n/hexo-asset-image --save（这是个修改过的插件，经测试无问题），使用这个插件来引入图片，而不是网上那些方法里说的用传统md语法相对路径的方法。

3. 插入图片时用这种方式：{% asset_img test.jpg This is an test image %}
　　其中test.jpg就是你要引用的图片，我这里就是test.jpg，后面的This is an test image是图片描述，可以自己修改。

4. 这样就能成功显示了，测试下吧：hexo cl && hexo g && hexo d
```

{% asset_img 1.png 图片显示测试 %}

### 第八步：hexo搜索功能

参考文章：https://www.jianshu.com/p/d388119a90ec

{%asset_img search.png hexo添加搜索功能%}

### 第九步: 博客首页截断显示

在需要截断的地方添加：

`<!--more-->`

### 第十步：修改博客字体

参考文章：https://blog.csdn.net/sailist/article/details/104114578

测试过文章中的方法，成功修改next主题的字体及字号！