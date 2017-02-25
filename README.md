# Jekyll ExtLinks
This Jekyll plugin adds custom attributes (`rel="nofollow"`, `target="_blank"`, etc.) to external links in your content.

## Description
This Jekyll plugin adds custom attributes to external links in your content. For example, you can add `rel="nofollow"` to all external links by default (with exceptions if you need them), or something like `class="external"`. You can also use it to add `target="_blank"` to external links, but generally it is not recommended as it leads to bad user experience. Multiple attributes are allowed.

## Installation
1. The Nokogiri gem is required (`gem install nokogiri`). If you experience any problems installing Nokogiri ("ERROR: Failed to build gem native extension", etc.), run `gem update --system` and try again. In case of a dependency error on Jekyll start ("cannot load such file -- nokogiri") add `gem 'nokogiri'` to your project's Gemfile.

2. Add this to your project's `Gemfile`:
  ```ruby
  gem 'jekyll-extlinks'
  ```

3. Add this to your project's `_config.yml`:
  ```yml
  gems:
    - jekyll-extlinks
  ```

## Configuration
Configure the plugin in your `_config.yml`. Notice the indentation matters. Example:

```yml
extlinks:
  attributes: {rel: nofollow, target: _blank}
  rel_exclude: ['host1.com', 'host2.net']
```

(`attributes` are required - at least one of them, `rel_exclude` is optional). Relative links will not be processed.
Links to hosts listed in `rel_exclude` will not have the `rel` attribute set. Links which have the `rel` attribute already will keep it unchanged, like this one in Markdown: `[Link text](http://someurl.com){:rel="dofollow"}`

Don't forget to actually use the plugin (see below).

## Usage
Use the plugin in your Jekyll layouts: `{{ content | extlinks }}`

## Notes
Developed by Dmitry Ogarkov - http://ogarkov.com/jekyll/plugins/extlinks/

Based on http://dev.mensfeld.pl/2014/12/rackrails-middleware-that-will-ensure-relnofollow-for-all-your-links/