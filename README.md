# NO LONGER MAINTAINED martinhartl.org Ghost theme

**This is a fork of [Sven Read's](https://github.com/starburst1977) awesome [Readium](https://github.com/starburst1977/readium) theme!**

My own blog [martinhartl.org](http://martinhartl.org) no longer uses Ghost, so this repository will not be updated in the future.

## Linkposts

I manually added support for link posts using this guide: [http://roaringapps.com/blog/link-posts-in-ghost/](http://roaringapps.com/blog/link-posts-in-ghost/)

In order to use link posts, add the following method to the core/server/helpers/index.js file of your Ghost installation

```javascript
coreHelpers.link = function (options) { 
   console.log("register link helper") 
    var txt = this.html,
        hasLink = txt.indexOf('<!-- link[') >= 0;

    if(hasLink) {
        this.theLink = txt.substring(txt.indexOf('<!-- link[') + 10, txt.indexOf('] -->', txt.indexOf('<!-- link[')));
        return options.fn(this);
    }
    else {
        return options.inverse(this);
    }
};
```

and register it in the `registerHelpers` function:

```javascript
registerThemeHelper('link', coreHelpers.link); 
```

Now, if you want to create a link post, just add `<!-- link[http://example.com] -->` to your post content, to link to use the headline of your post to link to the site.

## Thanks to:

- Bryce Cameron at [Roaring Apps](http://roaringapps.com/) for the [linkpost guide](http://roaringapps.com)
- rest coming soon

## License - MIT

Martin Hartl

Copyright (c) 2014 - 2015 Martin Hartl

Permission is hereby granted, free of charge, to any person
obtaining a copy of this software and associated documentation
files (the "Software"), to deal in the Software without
restriction, including without limitation the rights to use,
copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

