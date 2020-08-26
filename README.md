# jekyll-theme-console

A jekyll theme with inspiration from linux consoles for hackers, developers and script kiddies.

<img src="https://raw.githubusercontent.com/emoriarty/jekyll-theme-console/master/screenrec-dark.gif" width="550" title="Screenshot">

## Motivation

This is a fork from the original [jekyll-theme-console](https://b2a3e8.github.io/jekyll-theme-console) which I love but I think it needs a friendlier approach. Basically, a website is intended to be read over style, so I decided to apply some changes to improve readability without losing the hacky touch envisioned by [b2a3e8](https://github.com/b2a3e8).

The most important changes affect to paragraps, headlines and the navigation bar. There's also a new logo looking like a terminal prompt :)

## Demo

[dark style](https://b2a3e8.github.io/jekyll-theme-console-demo-dark/) ([source code](https://github.com/b2a3e8/jekyll-theme-console-demo-dark)):

[<img src="https://raw.githubusercontent.com/emoriarty/jekyll-theme-console/master/screenshot-dark.png" width="350" title="Screenshot">](https://b2a3e8.github.io/jekyll-theme-console-demo-dark/)


[light style](https://b2a3e8.github.io/jekyll-theme-console-demo-light/) ([source code](https://github.com/b2a3e8/jekyll-theme-console-demo-light)):

[<img src="https://raw.githubusercontent.com/emoriarty/jekyll-theme-console/master/screenshot-light.png" width="350" title="Screenshot">](https://b2a3e8.github.io/jekyll-theme-console-demo-light/)


[hacker style](https://b2a3e8.github.io/jekyll-theme-console-demo-hacker/) ([source code](https://github.com/b2a3e8/jekyll-theme-console-demo-hacker)):

[<img src="https://raw.githubusercontent.com/emoriarty/jekyll-theme-console/master/screenshot-hacker.png" width="350" title="Screenshot">](https://b2a3e8.github.io/jekyll-theme-console-demo-hacker/)


## Installation

First, follow the steps in [this Quickstart Guide](https://jekyllrb.com/docs/) if you're starting with Jekyll from scratch. Skip this if you already have an existing jekyll project.

**_You can also use the [demo site's source code](https://b2a3e8.github.io/jekyll-theme-console-demo-dark/) as template for an easy start._**

### Remote theme method

In order to install the current fork, you must use the [`jekyll-remote-theme`](https://github.com/benbalter/jekyll-remote-theme) gem. In your `_config_.yml` file you must define the option below.

```yaml
remote_theme: emoriarty/jekyll-theme-console
```

`jekyll-remote-theme` won't find the gems installed by the theme. The error thrown looks like below.

```shell
Dependency Error: Yikes! It looks like you don't have jekyll-seo-tag or one of its dependencies installed. In order to use Jekyll as currently configured, you'll need to install this gem. If you've run Jekyll with `bundle exec`, ensure that you have included the jekyll-seo-tag gem in your Gemfile as well. The full error message from Ruby is: 'cannot load such file -- jekyll-seo-tag' If you run into trouble, you can find helpful resources at https://jekyllrb.com/help/! 
```

To make it work, you must declare the [`jekyll-seo-tag`](https://github.com/jekyll/jekyll-seo-tag) manually in your `Gemfile`. You can see in the [`Gemfile`](https://github.com/emoriarty/jekyll-theme-console/blob/7c3f8773ab75903f6a66008b4ef1d938de94cd84/Gemfile#L7) to check for more plugins, if needed.

### Gem-based method

**The current fork has not been pushed to the ruby gems repository. Therefore, it cannot be installed as a gem.**

## Usage

### Shell Prompt Logo

The header logo looks like below.

```shell
[<prompt_name>:<prompt_path>]$
```

Where `prompt_name` is whatever name you like for your site, but in order to look like the bash prompt terminal it should be like `john@doe` or whatever `thing@thing` you like.

The `prompt_path` can be configured in any page. It is the actual path in the website. E.g. the `~` is user's home folder, so it can be used as the index page.

```shell
[john@doe:~]$
```

if `prompt_path` is defined in a layout and page frontmatter, the resulting prompt will be joined, forming a nested path.

```shell
[john@doe:/blog/my-first-post]$
```

In the example below, the post layout contains a `prompt_path` holding the `/blog` value while the post page holds `/my-first-post`.

### _config.yaml

In addition to jekyll's default configuration options, you can provide:
- `header_pages` to specify which pages should be displayed in navbar
- `footer` string, which will be inserted on the end of the page (doesn't support markup, but html)
- `google_analytics` tracking id (tracking will be enabled only in production environments and only if you set this option, no Google Analytics code will be loaded if you don't set this option)
- `listen_for_clients_preferred_style` boolean, used to allow users to choose light or dark style based on their preferences (mostly affected by OS dark or light theme, details see https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme)
- `style` to specify which predefined style (colors) should be used
- `prompt_name` specifies the name in the shell prompt logo.

```yaml
header_pages:
  - index.md
  - about.md

style: dark # dark (default), light or hacker
listen_for_clients_preferred_style: true # false (default) or true

prompt_name: john@doe
footer: 'follow us on <a href="https://twitter.com/xxx">twitter</a>'

google_analytics: UA-NNNNNNNN-N
```

### front matter variables

Besides the predefined [front matter](https://jekyllrb.com/docs/front-matter/) variables from jekyll this theme also supports following variables:
- `title` to set a title for the page
- `lang` to specify the language, defaults to 'en'
- `robots` to control the robot meta tag ([details](http://longqian.me/2017/02/12/jekyll-robots-configuration/)) - this may be useful for example to set `NOINDEX` to tag pages
- `prompt_path` specifies the current path in the shell prompt logo.

## Customization

If you want to customize this theme, follow this steps:
1. Fork this repository (you can use the fork as your own theme or directly as your website)
2. Create or modify files in `_layouts` directory for html-based changes
3. Create or modify files in `_sass` and `assets` for css-based changes
   - You can change things which are used in light and dark theme (like font-size) in `_sass/base.scss`. You'll find style variables at the top.
   - Style-specific definitions are in `_sass/_dark.scss` respectively in `_sass/_light.scss`. You can change things like background-color there.

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/b2a3e8/jekyll-theme-console. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.

## Development

To set up your environment to develop this theme, run `bundle install`.

Your theme is setup just like a normal Jekyll site! To test your theme, run `bundle exec jekyll serve` and open your browser at `http://localhost:4000`. This starts a Jekyll server using your theme. Add pages, documents, data, etc. like normal to test your theme's contents. As you make modifications to your theme and to your content, your site will regenerate and you should see the changes in the browser after a refresh, just like normal.

When your theme is released, only the files in `_layouts`, `_includes`, `_sass` and `assets` tracked with Git will be bundled.
To add a custom directory to your theme-gem, please edit the regexp in `jekyll-theme-console.gemspec` accordingly.

## License

The theme is available as open source under the terms of the [MIT License](https://opensource.org/licenses/MIT).
