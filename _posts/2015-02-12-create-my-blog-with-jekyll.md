---
layout: post
title:  "Jekyll Static build blog"
date:   2015-02-15 22:14:54
categories: jekyll
excerpt: Jekyll Github build static blog blog use high Yang Hao and Jia system to say Comments Share widget reference git tutorials
---

* content
{:toc}


## Ordre

Vous avez toujours voulu créer votre propre blog, mais au cours des six derniers mois est trop occupé pour faire le projet, en collaboration avec le Département du réseau est le père très au stand, il n'a pas de rechange. Auparavant, WordPress utilisé hébergé sur le moteur sans nuage Jingdong, mais trop lent. Nous voyons une partie du contenu sur le connu presque, il a donc choisi de construire sur le blog github avec jekyll.

---

## Processus de construction

Dans le site officiel de jekyll [http://jekyllrb.com/](http://jekyllrb.com/) est déjà un peu plus clair, et je suis ici ou parle tout simplement à ce sujet. J'utilise le système Windows.
Les principaux aspects sont les suivants: Installer Ruby, installer RubyGems, installez jekyll, le code soulignant installation plug-in, node.js d'installation

---

### Installer Ruby 

site officiel de rubis pour télécharger et installer：[https://www.ruby-lang.org/en/downloads/](https://www.ruby-lang.org/en/downloads/)

Configurer les variables d'environnement après l'installation est terminée

À l'invite de commande, obtenir ruby numéro de version, comme indiqué ci-dessous, que l'installation a réussi
![ruby-v]({{ "/css/pics/ruby-v.png"}})

---

### Installer RubyGems

Site officiel pour télécharger [http://rubygems.org/pages/download](http://rubygems.org/pages/download) rubygems-2.4.5.zip   

cd pour les RubyGems d'annuaire

![ruby-gems]({{ "/css/pics/ruby-gems.png"}})    

l'installation   

![ruby-gems-setup]({{"/css/pics/ruby-gems-setup.png"}})   

---

### With RubyGems installation Jekyll

Execute the following statement to install

![jekyll-setup]({{"/css/pics/jekyll-setup.png"}})   

End of Installation Screen

![jekyll-setup-finish]({{"/css/pics/jekyll-setup-finish.png"}})   

So far jekyll has been installed, and is the follow-up to their own personalized set.

---

### Create a blog

In the d disk to create a new workspace jekyll Workspace

cd 到 Jekyll Workspace

Executive jekyll new name to create a new workspace

![jekyllWorkSpace]({{"/css/pics/jekyllWorkSpace.png"}})   

File structure is as follows：   

![jekyllFiles]({{"/css/pics/jekyllFiles.png"}})

cd to the blog folder, turn on the server

![serve]({{"/css/pics/serve.png"}})   

watch in order to detect changes in the folder is, after modification does not need to restart jekyll

My environment started being given (you may not), then install yajl-ruby and rouge

![yajl]({{"/css/pics/yajl.png"}})

Start the server again successful

![serve-sucess]({{"/css/pics/serve-sucess.png"}})

access http://localhost:4000/   

![browser]({{"/css/pics/browser.png"}})   

Detailed article page

![browser2]({{"/css/pics/browser2.png"}})  

---

##Follow-up 

*  整个安装过程参考了jekyll官网，注意jekyll还有一个简体中文官网，不过比较坑（我就被坑了），有些内容没有翻译过来，有可能会走弯路，建议如果想看中文的相关资料，也要中英对照着阅读。[jekyll中文网 http://jekyllcn.com](http://jekyllcn.com), [jekyll英文网 http://jekyllrb.com](http://jekyllrb.com)
*  jekyll中的css是用sass写的，当然直接在`_sass/_layout.scss`中添加css也是可以的。
*  本文是用Markdown格式来写的，相关语法可参考： [Markdown 语法说明 (简体中文版) http://wowubuntu.com/markdown/](http://wowubuntu.com/markdown/)  
*  按照本文的说明搭建完博客后，用`github Pages`托管就可以看到了。注意，在github上面好像不支持rouge，所以要push到github上时，我将配置文件_config.yml中的代码高亮改变为`highlighter: pygments`就可以了
*  博客默认是没有评论系统的，本文的评论系统使用了多说，详细安装办法可访问[多说官网 http://duoshuo.com/](http://duoshuo.com/)，当然也可以使用[搜狐畅言 http://changyan.sohu.com/](http://changyan.sohu.com/)作为评论系统。	
*  也可以绑定自己的域名，如果没有域名，可以在[godaddy http://www.godaddy.com/](http://www.godaddy.com/)上将域名放入购物车等待降价，买之。
*  祝各位新年快乐！

---

## 可能出现的问题

### `hitimes/hitimes (LoadError)`

**错误代码：**

<pre><code class="markdown">C:/Ruby22/lib/ruby/2.2.0/rubygems/core_ext/kernel_require.rb:54:in `require': cannot load such file -- hitimes/hitimes (LoadError)</code></pre>

**解决方法：**

在stackoverflow上又一个很好的解决方法。[hitimes require error when running jekyll serve on windows 8.1](http://stackoverflow.com/questions/28985481/hitimes-require-error-when-running-jekyll-serve-on-windows-8-1) 虽然上面的题主问的是 win 8.1 系统下的情况，但是同样适用于 win7。下面我简单翻译一下错误原因和解决方法。

> 可能是 Ruby 2.2 和 hitimes-1.2.2-x86-mingw32 中有一些 ABI 变化，少了一些相关的类库。
> 
> 所以卸载 hitimes 并通过 `--platform ruby` 重装即可。代码如下：
>
><pre><code class="markdown">gem uni hitimes
**Remove ALL versions**
gem ins hitimes -v 1.2.1 --platform ruby
</code></pre>
> 然后将自动重新编译 hitimes 并适用于 Ruby 2.2

下面是我自己的卸载和安装过程：

<pre><code class="markdown">E:\GitWorkSpace\gaohaoyang.github.io>gem uni hitimes

You have requested to uninstall the gem:
        hitimes-1.2.2-x86-mingw32

timers-4.0.1 depends on hitimes (>= 0)
If you remove this gem, these dependencies will not be met.
Continue with Uninstall? [yN]  y
Successfully uninstalled hitimes-1.2.2-x86-mingw32

E:\GitWorkSpace\gaohaoyang.github.io>gem ins hitimes -v 1.2.1 --platform ruby
Fetching: hitimes-1.2.1.gem (100%)
Temporarily enhancing PATH to include DevKit...
Building native extensions.  This could take a while...
Successfully installed hitimes-1.2.1
Parsing documentation for hitimes-1.2.1
Installing ri documentation for hitimes-1.2.1
Done installing documentation for hitimes after 1 seconds
1 gem installed</code></pre>


关于，[hitimes](https://rubygems.org/gems/hitimes/versions/1.2.2) 是一个快速的高效的定时器解决方案库，详情可以去官网查看。


