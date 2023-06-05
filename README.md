# Starter Jekyll Devblog
Starter template for a student devblog based on the starter [Jekyll Minima theme](https://github.com/jekyll/minima).

This website starts with:

* An example blog post
* An placeholder project post
* Minimally formatted homepage, about page, blog page, projects page

Customizations include:

* Using collections instead of posts for greater flexibility
* Separate collections for Projects and Blog Posts
* Usage of Jekyll components (using `includes`) inspired by [React components](https://react.dev/learn/your-first-component)

## Usage
### Installation
Follow the [official documentation to install Jekyll](https://jekyllrb.com/docs/installation/). Be sure to install the required version of Ruby and follow the installation guide for your operating system.

### Code
Once you have installed Jekyll, [fork and clone](https://docs.github.com/en/get-started/quickstart/fork-a-repo) this repository onto your system. 

Using your terminal, navigate to the local folder containing your copy of this repository.

Run the `bundle install` command from your terminal.

To run a developer version, run `bundle exec jekyll serve`. In your browser, navigate to the `server address` that appears (it will likely be `localhost:4000`) to see a preview of your website.

### VSCode Codeblock Note
If you are using VSCode, in your `settings.json` file, copy and paste the following:
```
  "[markdown]": {
    "editor.formatOnSave": false,
  },  
```
This will turn off auto-formatting for your markdown files and ensure `codeblock` sections in your markdown files work properly&mdash;in practice, this mainly means preserving indentations.

### Publishing Your Site
There are two free and easy options to host your website for free:

- [Netlify](https://www.netlify.com/)
- [GitHub Pages](https://pages.github.com/)

#### [Netlify (Recommended)](https://www.netlify.com/blog/2020/04/02/a-step-by-step-guide-jekyll-4.0-on-netlify/)
I recommend using [Netlify to deploy your Jekyll site](https://www.netlify.com/blog/2020/04/02/a-step-by-step-guide-jekyll-4.0-on-netlify/) for greater flexibility; e.g. you can keep your repository private and customize the subdomain name to your liking. It is also currently easier to use&mdash;less setup required.

#### [GitHub Pages](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll)

The latest versions of Jekyll and Ruby are incompatible with the current version of GitHub Pages. If you decide to use GitHub pages, be sure to follow the official GitHub Docs to [create a GitHub Pages site with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll) and ensure [version compatibility](https://pages.github.com/versions/) in your `Gemfile`.

Note that to use GitHub Pages to host your website for free, your repository must be made public.
