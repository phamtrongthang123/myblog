# myblog

Everything inside content will be rendered to html. For example the file vitae.md is rendered into /vitae/index.html. 
For images, put them in static folder. Or else they wont be found after render. If you want to specify like html for img, use shortcode for it. Hugo builtin shortcode also support youtube video. And you can create custom shortcode. Very convenient.

Even I say that we may use shortcode, I know html, so I put 
```
markup:
  goldmark:
    renderer:
      unsafe: true # default is false
```
in the config.toml, so I can insert html whenever I want.

But raw html in the begining of md file is not allow, so we have to have some markdown write down first, for example I wrote `![]()` in the L1 of _index.md