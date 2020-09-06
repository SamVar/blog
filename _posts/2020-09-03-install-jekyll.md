---
layout: post
author: "Samvel Vardanyan"
title: "Install Jekyll"
date: 2020-09-03 15:15:49 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

**Install Jekyll on Mac**

Jekyll is very popular static site generator. It can be installed both on a Mac and Windows. In this section we'll talk about how to install it on a Mac. In order to install it on a Mac there are some steps that we need to follow. First we need to make sure that we have `rubby` installed on our system, Jekyll requires Ruby > 2.5.0. All Macs starting from catalina 10.15 come `ruby 2.6`. To check the which version `ruby` you are running,
open the terminal and type `ruby -v`, you will se something like this: `ruby 2.6.3p62 (2019-04-16 revision 67580)`, that means you have `ruby 2.6` installed. If you dont have `ruby` installed follow these steps:

\
Istall homebrew:
{% highlight ruby %}
/usr/bin/ruby -e "\$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

brew install ruby
{% endhighlight %}
\
Add the brew ruby path to your shell config:

{% highlight ruby %}
echo 'export PATH="/usr/local/opt/ruby/bin:\$PATH"' >> ~/.bash_profile
{% endhighlight %}

\
Close and reopen your terminal and check the updated version of `ruby`

{% highlight ruby %}
ruby -v
ruby 2.7.1p83 (2020-03-31 revision a0c7c23c9c)
{% endhighlight %}

\
Now you have `ruby` installed on your system.

\
Next step is to install `Bundler and Jekyll`
To install bundler and Jekyll open terminal and type the following command:

{% highlight ruby %}
gem install --user-install bundler jekyll
{% endhighlight %}
\
And now you have `ruby` and `Jekyll` installed on your system. You can open your code editor and open terminal inside of your code editor and type `jekyll new <blog-name>` (make sure to replace `<blog-name>` with any name that you would like to name your project). And if you would like to run your website just type the following command inside the terminal `bundle exec jekyll serve`, copy the address and paste it into your browser's web address bar. Usually the addres is `127.0.0.1:4000`.

That's it you are now runing jekyll site generator.

\
**Install Jekyl on Windows**

The easiest way to run Jekyll is by using the RubyInstaller for Windows. Follow the steps to install jekyll on windows:

1.  Download and Install a Ruby+Devkit version from [RubyInstaller](https://rubyinstaller.org/downloads/) Downloads. Use default options for installation.
2.  Run the `ridk` install step on the last stage of the installation wizard. This is needed for installing `gems` with native extensions.
3.  Open a command prompt, so that changes to the `PATH` environment variable becomes effective. After that install Jekyll and Bundler using `gem install jekyll bundler`.
4.  Type `jekyll -v` to check installed version of jekyll.

Now you have jakyll installed and ready to go on your system!

\
**Install Jekyll on Linux (Ubuntu)**

To install jekyll on ubuntu follow these steps: Open the terminal and type
{% highlight ruby %}
sudo apt-get install ruby-full build-essential zlib1g-dev
{% endhighlight %}
this will download all the dependancies necessary for the installation.
The following commands will add environment variables to your ~/.bashrc file to configure the gem installation path.
{% highlight ruby %}
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:\$PATH"' >> ~/.bashrc
source ~/.bashrc
{% endhighlight %}

And now we are ready to install jekyll on our system. Run the following commmand:
{% highlight ruby %}
gem install jekyll bundler
{% endhighlight %}

And finaly you have jekyll ready to go on your system.
