---
layout: post
title:  "How to Quickly Set Default Apps for File Types in macOS"
date:   2024-02-23 10:00:00 +0200
categories:  ["mac"]
---

## The Problem

I am working on a script that can configure a fresh macOS installation. One of the problems is to change what application is used to open files in Finder. You can use Finder UI `Get Info > Open with: -> Change All ...`, but it is cumbersome, and you also need a file with a specific extension to set it.

![Open with: UI](/images/openwith.png "Open with: UI")

## The solution

There is a better way. You can use utility called [duti](https://github.com/moretension/duti) that can set default applications for various document types on macOS. 

First you need to get bundle id for the app you want to open files with:

{% highlight bash %}
osascript -e 'id of app "Visual Studio Code"' # outputs: com.microsoft.VSCode
osascript -e 'id of app "Xcode"' # outputs: com.apple.dt.Xcode
{% endhighlight %}

Now install `duti`. I recommend installing with [homebrew](https://brew.sh).

{% highlight bash %}
brew install duti
{% endhighlight %}

Now you can easily set an application to open a specific file given its UTI (e.g., public.html), extension or MIME type:

{% highlight bash %}
duti -s com.microsoft.VSCode .sh all
duti -s com.microsoft.VSCode .markdown all
duti -s com.microsoft.VSCode .json all
duti -s com.microsoft.VSCode .yaml all
{% endhighlight %}

<!-- osascript -e 'id of app "Visual Studio Code"'
duti -s com.microsoft.VSCode .sh all -->

<!-- You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

Jekyll requires blog post files to be named according to the following format:

`YEAR-MONTH-DAY-title.MARKUP`

Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/ -->
