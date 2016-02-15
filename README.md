NimbleDroid Blog
----------------

This repository contains the sources of [http://blog.nimbledroid.com](http://blog.nimbledroid.com).

How to Add a Blog Post
--------

1. If you haven't already, clone the blog repository and install the gems.
Note that you need to install ruby before running `bundle`.

```
$ git clone git@github.com:NimbleDroid/nimbledroid.github.io.git
$ bundle install
```

2. Go to the local clone of the repo, and create a post `my-post-topic.md`
in `_drafts`.  Your draft post should follow the [markdown
syntax](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
with a [front mater](http://jekyllrb.com/docs/frontmatter/) specifying
things such as post layout and title.

3. Run `jekyll serve --watch --drafts` and then visit
`http://localhost:4000` to check out your draft.  (The `--watch` option
tells `jekyll` to monitor your directory and refresh the site if there's
any change, and the `--drafts` option tells `jekyll` to include `_drafts`
in addition to `_posts` in the site.) Continue revising your draft until
you're ready to publish it.

4. If you need to share your post with someone before publishing it, you
can commit and push your post to github.  As long as the post remains in
the `_drafts` directory, it won't be displayed on our public blog site.
In addition, if you want to share the post with someone who doesn't have
github access, you can move the post to `_posts/en` but add `visible:
false` to the post's front matter.

5. Once the post is ready: Move the draft to `_posts/en` (if in English),
`_posts/ru` (if in Russian), or `_posts/zh` (if in Chinese). The name
should follow `yyyy-mm-dd-my-post-topic[-lang].md`. Note that if language
is in English, omit [-lang]; otherwise, append the two-letter language
code (e.g., -zh for Chines).  Add an appropriate language to the post's
front matter, using `lang: English`, `lang: Русский`, or `lang: 中文`. You
must also specify a unique `name: ` in the post's front matter. For a
translated version of a post, be sure to set the `name: ` to the same
value it has in the English version. Be sure to set `visible: true`.


Aside Menu Configuration:
--------
1. The aside menu contains site description, which is in '_config.yml' 'descriptionfull'
2. The
