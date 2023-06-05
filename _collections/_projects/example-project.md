---
layout: post
title: "Example Project: Python Snippet"
description: Example project post showing Python code snippets.
technologies: [Python]
---

This is an example of what a project page might look like.

When you talk about a project, you want to cover two things:

1. What is the project?
  - Does it solve any problem?
  - Why did you do it?
2. How did you build it?
  - What technologies did you use?
  - What challenges/interest problems did you encounter?
  - What did you learn?

## What Is the Project?
Let's talk about what it is.

## How Did I Build the Project?

I built the Project with: 

{% for technology in page.technologies %}
- {{ technology }}
{% endfor %}

Something cool I did:

```python
def do_something_cool(a_variable):
  return a_variable

def some_cool_function(some_cool_vars):
  some_cool_out = do_something_cool(some_cool_vars)
  return some_cool_out
```

