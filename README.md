# Starter Jekyll Devblog
Starter template for a student devblog based on the starter [Jekyll Minima theme](https://github.com/jekyll/minima).

View live version here: [live-preview]

This repository gets you started with:

* Minimally formatted placeholder:
  * Homepage
  * About page
  * Blog page
  * Projects page
* An example blog post
* An placeholder project post
* A placeholder portrait (red panda!)

Customizations include:

* Using collections instead of posts for greater flexibility
* Separate collections for Projects and Blog Posts
* Usage of Jekyll components (using `includes`) inspired by [React components](https://react.dev/learn/your-first-component)

## Usage
### Installation
Follow the [official documentation to install Jekyll](https://jekyllrb.com/docs/installation/). Be sure to install the required version of Ruby and follow the installation guide for your operating system.

**Make sure you install the versions of Ruby and Jekyll that are [compatible][github-jekyll-versioning] with your [chosen hosting solution](#publishing-your-site).**

### Using This Repository
After you have installed Ruby and Jekyll, following the docs for either Jekyll or GitHub pages,

1. [Fork and clone](https://docs.github.com/en/get-started/quickstart/fork-a-repo) this repository onto your system. 
2. Using your terminal, navigate to the local folder containing your copy of this repository.
3. Run the `bundle install` command from your terminal.

You are now free to make changes to the website!

To preview your website in developer mode:

1. Run `bundle exec jekyll serve`. 
2. In your browser, navigate to the `server address` that appears (it will likely be `localhost:4000`).

### VSCode Markdown Codeblocks
If you are using [VSCode](https://code.visualstudio.com/), in your `settings.json` file, copy and paste the following:

```
  "[markdown]": {
    "editor.formatOnSave": false,
  },  
```

This will turn off auto-formatting for your markdown files and ensure `codeblock` sections in your markdown files work properly&mdash;in practice, this mainly means preserving indentations.

## Publishing Your Site
There are two free and easy options to host your website for free:

- [Netlify](https://www.netlify.com/)
- [GitHub Pages](https://pages.github.com/)

### [Netlify (Recommended)][netlify-setup-guide]
I recommend using [Netlify to deploy your Jekyll site](https://www.netlify.com/blog/2020/04/02/a-step-by-step-guide-jekyll-4.0-on-netlify/).

* It's a more flexible solution (e.g. you can keep your repository private and customize the subdomain name to your liking).
* It is currently easier to use&mdash;there is less setup required, as you do not need to worry about version compatibility in your `Gemfile` unless you add additional Gems.

### [GitHub Pages][github-pages-guide]

The latest versions of Jekyll and Ruby are incompatible with the current version of GitHub Pages. If you decide to use GitHub pages, be sure to follow the official GitHub Docs to [create a GitHub Pages site with Jekyll][github-pages-guide] and ensure [version compatibility][github-jekyll-versioning] in your `Gemfile`.

Note that to use GitHub Pages to host your website for free, your repository must be made public.

Happy building!


[live-preview]: https://devblog-starter-jekyll.netlify.app
[github-jekyll-versioning]: https://pages.github.com/versions/
[netlify-setup-guide]: https://www.netlify.com/blog/2020/04/02/a-step-by-step-guide-jekyll-4.0-on-netlify/
[github-pages-guide]: https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll