---
title: Code
sections:
- Setup
- First component
- LESS
- Sass
- JavaScript
- Python
- PHP
- Handlebars
- Git
---

[PrismJS](http://prismjs.com/) is used as the syntax highlighter here.
You can [build your own version](http://prismjs.com/download.html) via their website should you need to.

<div class="callout-block callout-success"><div class="icon-holder">
*&nbsp;*{: .fa .fa-thumbs-up}	
</div><div class="content">
{: .callout-title}
Useful Tip:

You can use this online [Component builder](/builder)
to experiment before committing to code.
</div></div>


{: #Setup}
In your entry file (for exmple `/index.html`) initialize your application as follows
- create an element with the name of your choise. in this example we use `mynamespace-myawesomecomponent`
- initialize js, in this case we use inline code, but a separate file would work just fine as wel (NOTE: it has to be an module to allow `import`s)
- impport the `Component` and `Composer` classes
- register namespaces with the `Composer` class by calling `register` and passing it an object with a `namespace: resolver` structure. Since the `Suite` could be anywhere we need to both register the suite and our own namespace (NOTE: the suite must fall under the namespace `fyn` because otherwise all internal calls will go wrong, this will be fixed in the future)
- finally load your component with `Component.load`

```html
<mynamespace-myawesomecomponent></mynamespace-myawesomecomponent>

<script type="module">
  import Component from '/node_modules/@fyn-software/component/component.js';
  import Composer from '/node_modules/@fyn-software/component/composer.js';

  Composer.register({
      fyn: (n, t) => `/node_modules/@fyn-software/suite/${t}/${n.join('/')}.${t}`,
      mynamespace: (n, t, ns) => `/${t}/${ [ns, ...n].join('/')}.${t}`,
  });

  Component.load('mynamespace-myawesomecomponent');
</script>
```

Next up is to create the code behind your component
- Create a file `/js/mynamespace/myawesomecomponent.js`.
- Import `fyn.js` and 'types.js' files.
- Create a class with the name of you component in Pascal-casing.
- Extend it from `FYN.Component`.
- (Optional) Implement a static getter with the name `properties`, this getter return an object with the properties of your component.
- (Optional) Implement a method called `ready`, this method is called by `FYN.Component` when it is done initializing the properties and the template.

`/js/mynamespace/myawesomecomponent.js`
```js
import * as FYN from '/node_modules/@fyn-software/component/fyn.js';
import * as Types from '/node_modules/@fyn-software/data/types.js';

class MyAwesomeComponent extends FYN.Compontent
{
  static get properties()
  {
      return {
          title: Types.String.default('This is my awesome component'),
      };
  }

  ready()
  {
      this.on({
          click: (e, t) => this.animate('flash'),
      });
  }
}
```

Finally let us create the template for our component.
- Create the following file `/html/mynamespace/myawesomecomponent.html`.
- (Optional) Import the style from the Suite to get a normalized head start
- (Optional) Create a style element to create some visual interest for your component
- Add the markup for your component, you may render the components properties by creating a mustache tag (`{{  }}`) and filling in the name of the property.

```html
<link rel="stylesheet" type="text/css" href="/node_modules/@fyn-software/suite/css/style.css">
<style>
  :host {
      display: grid;
      grid-auto-flow: row;
      grid-gap: 1em;
  }
</style>

<h1>{{ title }}</h1>

```

Done! This is the minimal boilerplate.

{: #css}
###### CSS Code Example

```css
/* ======= Base Styling ======= */
body {
    font-family: 'Open Sans', arial, sans-serif;
    color: #333;
    font-size: 16px;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}
```


{: #less}
###### LESS Code Example

```css
/*
* Template Name: prettyDocs - Responsive Website Template for documentations
* Version: 1.0
* Author: Xiaoying Riley
* License: Creative Commons Attribution 3.0 License
* Twitter: @3rdwave_themes
* Website: http://themes.3rdwavemedia.com/
*/
@import "mixins.less";
@import "theme-default.less";
@import "base.less";
@import "doc.less";
@import "landing.less";
@import "responsive.less";
```


{: #sass}
###### Sass Code Example

```sass
#main {
    $width: 5em;
    width: $width;
}

#sidebar {
    width: $width;
}
```


{: #javascript}
###### JavaScript Code Example

```javascript
<script>
    function myFunction(a, b) {
        return a * b;
    }

    document.getElementById("demo").innerHTML = myFunction(4, 3);
</script>
```


{: #python}
###### Python Code Example

```python
>>> x = int(input("
Please enter an integer: ")) Please enter an integer: 42
>>> if x < 0:
... x = 0
... print('Negative changed to zero')
... elif x == 0:
... print('Zero')
... elif x == 1:
... print('Single')
... else:
... print('More')
... More
```


{: #php}
###### PHP Code Example

```php
<?php
$txt = "Hello world!";
$x = 5;
$y = 10.5;

echo $txt;
echo "<br>";
echo $x;
echo "<br>";
echo $y;
?>
```


{: #handlebars}
###### Handlebars Code Example

```handlebars
Handlebars.registerHelper('list', function(items, options) {
  var out = "<ul>";

  for(var i=0, l=items.length; i<l; i++) {
    out = out + "<li>" + options.fn(items[i]) + "</li>";
  }

  return out + "</ul>";
});
```


{: #git}
###### Git Code Example

```shell
$ git add Documentation.txt
```
