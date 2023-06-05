---
layout: post
title: 'Example Blog Post: Jekyll "Components"'
description: An example blog post that introduces a technique for building components in Jekyll.
canonical_url: "alexye.me/blog/how-to-create-jekyll-components/"
---

This is an example of a blog post you might include in your dev blog. You can write about anything programming/software-engineering-related; it can be a solution for a challenge you encountered, an interesting problem you came across, or something along those lines. 

Your posts don't have to be as involved as this, but I figured this topic would make for a good example&mdash;after all, if you poke through this website's GitHub repository, you'll find that we build [React-inspired][react-components] components using Jekyll's `include` feature.

## What Is a Component in Web Development?

In web development, the term "component" refers to an independent and reusable block of code that returns a UI element. 

Unlike old-school or "traditional" web development, which organized code based on technologies and languages&mdash;HTML for templating and semantic tagging, CSS for styling, and JavaScript for scripting and logic&mdash;components encourage organizing code by UI elements. 

Nowadays, developers commonly combine semantic tags, styling tools, and scripting languages when creating applications. The goal is to create reusable UI elements in a way that reduces redundant code and more intuitively organizes a codebase.

The use of components is now a standard paradigm in software development. Examples of mainstream frameworks that encourage a developer organize their code around UI components include:

* [React](https://react.dev/) and [Vue](https://vuejs.org/), which use [Components](https://developer.mozilla.org/en-US/docs/Web/API/Web_components).
* [Flutter](https://flutter.dev/), which uses [Widgets](https://docs.flutter.dev/ui/widgets-intro).
* [Jekyll](https://jekyllrb.com/), which uses [`includes`](https://jekyllrb.com/docs/liquid/tags/#includes), the topic of this post.


## [Jekyll Includes](https://jekyllrb.com/docs/includes/)
Jekyll provides a tag, `include`, you can use in your HTML and Markdown files to "include" (get it?) "components" in your website code. 

A common use-case for `include` is to create template code for content that will exist globally&mdash;for instance, site footers, site headers, navigation menus, logos, and so on. 

Jekyll will automatically detect and allow you to reference HTML files you create in a folder called `_includes`, which you can create in your project's root directory. 

Following programming best practices, Jekyll's `include` lets you store and reference reusable blocks of code instead of having you copy and paste cumbersome sections of duplicate code (which also means having to modify code in various places if changes must be made to this content).

### An Example: Site Navigation
The `_includes` directory for a basic Jekyll website might look like this:

```
_includes/
  components/
    post-card.html
    project-card.html
  site/
    footer.html
    head.html
    header.html
    navigation.html
```

The `navigation.html` file in `_includes/site` might look like this:
```liquid
<!-- _includes/site/navigation.html -->
<!-- Style tags removed -->
<nav>
  <div>
    <a href="/">
      <h1>Your Site Title</h1>
    </a>
  </div>
  <ul>{% raw %}
    {% for item in site.data.navigation %}
      <li>
        <a href="{{ item.link }}">
          {{ item.name }}
        </a>
      </li>
    {% endfor %}{% endraw %}
  </ul>
</nav>
```

For your average website, we'd want the navigation to be accessible from every page. Without Jekyll's `include` functionality, we would need to copy and paste the code above everywhere we want the site navigation to show up&mdash;and if we ever wanted to change the code, we'd need to make modifications everywhere we paste it. 

Don't do that.

Instead, use the power of Jekyll and place the code for the site navigation in the `_includes` folder. 

Following the directory structure above, we can conveniently place the site navigation wherever we want on our website with the following code snippet in any relevant HTML file: 

{% raw %}`{% include site/navigation.html %}`{% endraw %}

As an example:
```liquid
<header>{% raw %}
  {% include site/navigation.html %}{% endraw %}
</header>
```

<!-- [display liquid code](https://michaelcurrin.github.io/dev-cheatsheets/cheatsheets/jekyll/code-blocks/liquid-code.html) -->

## Building Components With `include`
Nice, so we can implement reusable blocks of code using Jekyll's `include` functionality. But what if we want each instance of a block to be slightly different, depending on where/how we use it?

Let's take a look at an example of what we're talking about with a React example.

### React Components
If you're familiar with React, you know that you can build reusable components&mdash;such as a site navigation component. 

React components are a bit more involved than Jekyll Includes; whereas Jekyll only requires basic HTML and Liquid (if you want), React requires you to define functions that return elements in `.jsx` files.

The same site navigation, but in React:

```jsx
// In SiteNavigation.jsx
// Let's assume the navigation data is in a navigation.js file:
import links from '/path/to/site/data/navigation.js';

export default const SiteNavigation = () => {
  return <nav>
    <div>
      <a href="/">
        <h1>Your Site Title</h1>
      </a>
    </div>
    <ul>
    {links.map((item) => {
      return <li>
          <a href={item.link}>
            {item.name}
          </a>
        </li>
    })}
    </ul>
  </nav>
}
```

And wherever we want the site navigation to appear, in React we would write:

```jsx
import SiteNavigation from 'path/to/SiteNavigation.jsx';

// ... some code ...
<header>
  <SiteNavigation />
</header>
```

But components don't have to be static; we can modify them depending on what we need them to do and how we want them to look. One way to accomplish this is to use props.

For instance, let's say I had a blog and wanted to render a collection of blog cards&mdash;one for each post, where each post has a different title, url, description, and topic. 

A simple component we might build to accommodate this might look like this:

```jsx
// In PostCard.jsx
// Without styling
export default const PostCard = (
  {title, 
   description, 
   url, 
   topic}) => {
  return <a href={url}>
  <article>
    <h2>{title}</h2>
    <p>{description}</p>
    <p>{topic}</p>
  </article>
</a>
}
```

To render these blog cards somewhere, we might write something like this:
```jsx
import PostCard from "/directory/pointing/to/PostCard.jsx"

// ... some code ...
// Assuming we have posts in an array called site.posts, 
// as Jekyll does by default
site.posts.map((post) => {
  const { title, description, url, topic} = post
  return <PostCard 
    title={title}
    description={description}
    url={url}
    topic={topic}
  >
})
```

The code above iterates over the `site.posts` array and renders our `PostCard` element. 

Unlike the code for our site navigation, which will render the same UI element every time, `PostCard` will render something different in our UI depending on the data it receives via props.

Neat. How do we accomplish this in Jekyll?

### Building "Components" In Jekyll
Jekyll's `include` functionality can be leveraged to build React-like components, and we can actually replicate the props approach when we do this.

<!-- In React, projects are often organized to include a folder called `components`. This folder, as its name implies, is meant to store all the reusable components a web developer might end up leveraging for their project. We can consider the `_includes` folder as Jekyll's version of a `components` folder; again, Jekyll automatically detects and allows you to use .html files you create in this folder. -->

Let's say we wanted to render blog cards with the same specifications as the React code: We want to render a collection of blog cards&mdash;again, one for each post, where each post has a different title, url, topic, and description in its [frontmatter](https://jekyllrb.com/docs/front-matter/).

Without any component voodoo, we'd write something this:

```liquid{% raw %}
{% for post in site.posts %}
  <a href="{{ post.url }}">
    <article>
      <h2>{{ post.title }}</h2>
      <p>{{ post.description }}</p>
    </article>
  </a>
{% endfor %}{% endraw %}
```

This seems fine. But what if our blog covers multiple topics, and we wanted each topic to get a page filled with blog cards for just that topic? With the above approach, we'd copy and paste the code for every topic:

```liquid{% raw %}
{% for post in site.posts %}
  {% if post.topic == 'some_topic' %}
    <a href="{{ post.url }}">
      <article>
        <h2>{{ post.title }}</h2>
        <p>{{ post.description }}</p>
        <p>{{ include.topic }}</p>
      </article>
    </a>
  {% endif %}
{% endfor %}{% endraw %}
```

And if we wanted to change something about the blog cards with this approach, we'd need to edit the block of code everywhere we paste it. Annoying.

Instead, let's move the block of code into a file in our `_includes` folder:

```liquid{% raw %}
<!-- in _includes/components/post-card.html -->
<a href="{{ include.url }}">
  <article>
    <h2>{{ include.title }}</h2>
    <p>{{ include.description }}</p>
    <p>{{ include.topic }}</p>
  </article>
</a>{% endraw %}
```

When we componentize our card in this way, we can easily render a collection of post cards like so:
```liquid{% raw %}
{% for post in site.blog %}
  {% include components/post-card.html
      title = post.title
      description = post.description
      url = post.url
      topic = post.topic
    %}
{% endfor %}{% endraw %}
```

The syntax is slightly different between Jekyll and React, but the approach is exactly the same: we pass "props" into our `includes` component. And when we organize our code this way, whenever we want to make changes to our blog card, in most cases we'd really only need to modify code one place.

Happy building!


[reference-guide]: https://sayzlim.net/jekyll-include-component/
[react-components]: https://react.dev/learn/your-first-component