---
layout: home
title: Home
tagline: FYN Software's webcomponent suite
heading: Getting started is easy!
navigation:
  - /start
  - /components
  - /charts
  - /faqs
  - /showcase
  - /credits
  - /news
  - /community
  - /legal
---

Start building your awesome web app powered by a simple yet powerful suit.

<div class="text-left">
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

  `/html/mynamespace/myawesomecomponent.html`
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

  `/index.html`
  ```html
  <mynamespace-myawesomecomponent></mynamespace-myawesomecomponent>

  <script type="module">
      import Component from '/node_modules/@fyn-software/component/component.js';
      import Composer from '/node_modules/@fyn-software/component/composer.js';

      Composer.register({
          fyn: (n, t) => `/node_modules/@fyn-software/suite/${t}/${n.join('/')}.${t}`,
          toolkit: (n, t, ns) => `/${t}/${ [ns, ...n].join('/')}.${t}`,
      });

      Component.load('mynamespace-myawesomecomponent');
  </script>
  ```
</div>

<div class="cta-container">

[*&nbsp;*{: .fa .fa-github} Core][CORE]{: .btn .btn-blue .btn-primary .btn-cta}
[*&nbsp;*{: .fa .fa-github} Component][COMP]{: .btn .btn-green .btn-primary .btn-cta}
[*&nbsp;*{: .fa .fa-github} Data][DATA]{: .btn .btn-magenta .btn-primary .btn-cta}
[*&nbsp;*{: .fa .fa-github} Suite][SUITE]{: .btn .btn-orange .btn-primary .btn-cta}

</div>

[CORE]: https://github.com/FYN-Software/core
[COMP]: https://github.com/FYN-Software/component
[DATA]: https://github.com/FYN-Software/data
[SUITE]: https://github.com/FYN-Software/suite
