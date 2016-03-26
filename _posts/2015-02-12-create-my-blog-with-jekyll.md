---
layout: post
title:  "Jekyll Static build blog"
date:   2015-02-15 22:14:54
categories: jekyll
excerpt: Jekyll Github build static blog blog use high Yang Hao and Jia system to say Comments Share widget reference git tutorials
---

* content
{:toc}


## Order

Always wanted to set up your own blog, but over the past six months is too busy to do the project, together with the Department of the network is very pit father, so it has no spare. Previously used WordPress hosted on free Jingdong cloud engine, but too slow. We see some of the content on the known almost, so he chose to build on github blog with jekyll.

---

## Building process

In jekyll's official website [http://jekyllrb.com/](http://jekyllrb.com/) is already a little more clear, and I am here or simply talk about it. I use the Windows system.
The main aspects are: Install Ruby, install RubyGems, install jekyll, code highlighting plug-in installation, installation node.js

---

### Installing Ruby

ruby official website to download and install: [https://www.ruby-lang.org/en/downloads/](https://www.ruby-lang.org/en/downloads/)

Configure the environment variables after the installation is complete

At the command prompt, get ruby ​​version number, as shown below, that the installation was successful
![Ruby-v]({{ "/css/pics/ruby-v.png"}})

---

### Installed RubyGems

Official website to download [http://rubygems.org/pages/download](http://rubygems.org/pages/download) rubygems-2.4.5.zip

cd to the directory RubyGems

![Ruby-gems]({{ "/css/pics/ruby-gems.png"}})

The installation

![Ruby-gems-setup]({{ "/css/pics/ruby-gems-setup.png"}})

---

### With RubyGems installation Jekyll

Execute the following statement to install

![Jekyll-setup]({{ "/css/pics/jekyll-setup.png"}})

End of Installation Screen

![Jekyll-setup-finish]({{ "/css/pics/jekyll-setup-finish.png"}})

So far jekyll has been installed, and is the follow-up to their own personalized set.

---

### Create blog

In the d disk to create a new workspace jekyllWorkspace

cd to jekyllWorkspace

Executive jekyll new name to create a new workspace

![JekyllWorkSpace]({{ "/css/pics/jekyllWorkSpace.png"}})

File structure is as follows:

![JekyllFiles]({{ "/css/pics/jekyllFiles.png"}})

cd to the blog folder, turn on the server

![Serve]({{ "/css/pics/serve.png"}})

watch in order to detect changes in the folder is, after modification does not need to restart jekyll

My environment started being given (you may not), then install yajl-ruby and rouge

![Yajl]({{ "/css/pics/yajl.png"}})

Start the server again successful

![Serve-sucess]({{ "/css/pics/serve-sucess.png"}})

Visit http: // localhost: 4000 /

![Browser]({{ "/css/pics/browser.png"}})

Detailed article page

![Browser2]({{ "/css/pics/browser2.png"}})

---

## Follow-up

* The entire installation process with reference to the official website jekyll, jekyll note there is a Simplified Chinese official website, but more pit (I was pit), some content is not translated, there may be detours, I suggested that if the Chinese want to see the relevant information, but also according to Britain to read. [Jekyll Chinese network http://jekyllcn.com] (http://jekyllcn.com), [jekyll English network http://jekyllrb.com] (http://jekyllrb.com)
* Jekyll the css sass is written, of course, add css directly in `_sass / _layout.scss` it is also possible.
* This article is written using Markdown format, the relevant reference syntax: [Markdown syntax description (Simplified Chinese Version) http://wowubuntu.com/markdown/](http://wowubuntu.com/markdown/)
* After following the instructions in this article to build a complete blog, hosted by `github Pages` can see. Note that the rouge on github seems not to support it, so to push to github, I will profile _config.yml code highlighting changed to `highlighter: pygments` it
* The default is no blog comment system, this paper reviews the system used to say, a way to access detailed installation [say official website http://duoshuo.com/](http://duoshuo.com/), of course, can use [Sohu Chatteris http://changyan.sohu.com/](http://changyan.sohu.com/) as a commenting system.
* You can also bind your own domain name, the domain name if not, you can [godaddy http://www.godaddy.com/](http://www.godaddy.com/) will wait for prices Add to Cart Domain, Buy it.
* I wish you a Happy New Year!

---

## Problems that may arise

### `Hitimes / hitimes (LoadError)`

**error code:**

<pre><code class = "markdown"> C:/Ruby22/lib/ruby/2.2.0/rubygems/core_ext/kernel_require.rb: 54: in `require ': can not load such file - hitimes / hitimes (LoadError ) </code></pre>

**Solution:**

On stackoverflow and a good solution. [Hitimes require error when running jekyll serve on windows 8.1](http://stackoverflow.com/questions/28985481/hitimes-require-error-when-running-jekyll-serve-on-windows-8-1) Although the above the main question to ask is the case under the win 8.1 system, but applies equally to win7. Now I simply translate the error causes and solutions.

> Might be Ruby 2.2 and hitimes-1.2.2-x86-mingw32 ABI has some changes, some less relevant libraries.
>
> Uninstall hitimes so by `--platform ruby` to reload. Code is as follows:
>
> <pre><code class = "markdown"> gem uni hitimes
** Remove ALL versions **
gem ins hitimes -v 1.2.1 --platform ruby
</code></pre>
> Then automatically recompile hitimes and applies to Ruby 2.2

Here is my own uninstall and installation process:

<pre><code class = "markdown">E:\GitWorkSpace\gaohaoyang.github.io>gem uni hitimes

You have requested to uninstall the gem:
        hitimes-1.2.2-x86-mingw32

timers-4.0.1 depends on hitimes (> = 0)
If you remove this gem, these dependencies will not be met.
Continue with Uninstall? [YN] y
Successfully uninstalled hitimes-1.2.2-x86-mingw32

E: \ GitWorkSpace \ gaohaoyang.github.io> gem ins hitimes -v 1.2.1 --platform ruby
Fetching: hitimes-1.2.1.gem (100%)
Temporarily enhancing PATH to include DevKit ...
Building native extensions. This could take a while ...
Successfully installed hitimes-1.2.1
Parsing documentation for hitimes-1.2.1
Installing ri documentation for hitimes-1.2.1
Done installing documentation for hitimes after 1 seconds
1 gem installed </code></pre>


On, [hitimes](https://rubygems.org/gems/hitimes/versions/1.2.2) is a fast and efficient solution for timer library, you can view the details Quguan network.
