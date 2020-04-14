# JAVASCRIPT

<!--[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)-->

<!--[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)-->

### POLYFILL BUILDER
[https://cdn.polyfill.io/v3/url-builder/](https://cdn.polyfill.io/v3/url-builder/)

### JS Rotate Vertical or Horizontal
[https://developer.mozilla.org/en-US/docs/Web/API/Window/orientationchange_event](https://developer.mozilla.org/en-US/docs/Web/API/Window/orientationchange_event)

### LARAVEl MIX WEBPACK
```sh
Images: <%= mix('/assets/images/sample.gif') %>
Svg <%= svgSprite('/assets/svg/sprite.svg', '#sprite-sample-a') %>
```

### GET BOUNDING RECT
```sh
wrap.style.top = `${wrap.getBoundingClientRect().top}px`;
```

### COUNTING FOREACH and starts at a specific number

```sh
annualEventMonthRow.forEach(function(e, i) {
  let max = 12;
  let start = 4 + i;
  let txt = '';

  if(start <= max) {
    text = start + '月';
  } else {
    text = (start-max) + '月';
  }

  e.innerHTML = text;

});
```

### IMPORTING SVG SPRITE

```sh
<script src="<?php echo resolve_asset_url( '/lib/svg4everybody.js' ); ?>"></script>
<script>svg4everybody();</script>
```

Root folder
svg-sprite-config.json
```sh
{
  "dest": "wp/wp-content/themes/seika-kindergarten/assets/svg",
  "mode": {
    "symbol": {
      "dest": ".",
      "sprite": "icons.svg"
    }
  }
}
```
Icon.php on theme’s folder

```sh
<svg role="img">
  <use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="<?php echo resolve_svg_url( 'icons.svg#src--seika-kindergarten--svg--'.$icon ); ?>"></use>
</svg>
```
Package.json

```sh
"start": "npm run build && npm run svgsprite && npm run serve",
"svgsprite": "svg-sprite -C svg-sprite-config.json './src/seika-kindergarten/svg/*.svg'"
```


### WRAP KEY ONLY FOR KEBAB CASE in EJS FORMAT

```sh
<%
data1 = [{
   key: '...',
   camelCase: '...'
}]
data2 = [{
   key: '...',
   'kebab-case': '...'
}]
%>
```

### SCROLL X FIXED HEADER

```sh
header = document.querySelector('#js-header');

let ticking = false;
let lastScrollLeft = 0;
window.addEventListener('scroll', function() {
  let el = this;
  if (!ticking) {
      window.requestAnimationFrame(function() {
          let documentScrollLeft = CONST.$document.scrollLeft();
          if (lastScrollLeft != documentScrollLeft) {
            lastScrollLeft = documentScrollLeft;

            let scrollXValue = ((el.scrollX || el.pageXOffset));
            header.style.left = `-${scrollXValue}px`;
          }
          ticking = false;
      });
    ticking = true;
  }
});

```

### MEDIA QUERY

```sh
let mediaQuery = window.matchMedia('(max-width: 767px)');

headerNavController(mediaQuery); // create controller
mediaQuery.addListener(headerNavController);

function headerNavController({ matches }) {
  if ( matches ) {
    headerBurger.addEventListener('click', function(e) {
      e.preventDefault()

      header.classList.toggle(CONST.IS_FIXED)
      burger.classList.toggle(CONST.IS_ACTIVE)
      headerNav.classList.toggle(CONST.IS_ACTIVE)

      if(headerNav.classList.contains(CONST.IS_ACTIVE)) {
        scrollLock()
      } else {
        scrollAble()
      }

    });
  } else {
    header.classList.remove(CONST.IS_FIXED)
    burger.classList.remove(CONST.IS_ACTIVE)
    headerNav.classList.remove(CONST.IS_ACTIVE)

    scrollAble();
  }
}

```


### WINDOW SCROLL TO CONTENT PURE JS

```sh
window.addEventListener('load', (e, i) => {
  let thisWindow = e.currentTarget;
  const hash = location.hash;
  const yCoordinate = document.querySelector(hash).getBoundingClientRect().top + window.pageYOffset;

  if ( hash !== null) {
    thisWindow.scrollTo({
        top: yCoordinate,
        behavior: 'smooth'
    });
  }
});
```


### BUTTON CLICKED SCROLL TO CONTENT PURE JS

const button = document.querySelector('.js-scroll-button');

```sh
button.addEventListener('click', function(e, i) {
  e.preventDefault();
  const hash = e.currentTarget.getAttribute('href');
  const yCoordinate = document.querySelector(hash).getBoundingClientRect().top + window.pageYOffset;

  if ( hash !== null) {
    window.scrollTo({
        top: yCoordinate,
        behavior: 'smooth'
    });
  }
});
```

### GSAP
Must install imports-loader for gsap

```sh   
require('imports-loader?define=>false!scrollmagic/scrollmagic/uncompressed/plugins/animation.gsap');
```

### IE ISSUES USE POLYFILL

```sh
<script src="https://cdn.polyfill.io/v2/polyfill.min.js"></script>

'use strict';

if (!NodeList.prototype.forEach) {
  NodeList.prototype.forEach = Array.prototype.forEach;
}
```

### SCROLL LOCK

```sh
import {$document, $window, ACTIVE_CLASS} from '../constants/';

const wrap = document.querySelector('#js-wrap');

let scrollTop = 0;
export const ableScroll = () => {

   wrap.classList.remove(ACTIVE_CLASS);
   wrap.style.top = '';

   document.documentElement.scrollTop = scrollTop;
 }

export const lockScroll = () => {
  scrollTop = document.documentElement.scrollTop;

  wrap.classList.add(ACTIVE_CLASS);
  wrap.style.top = `-${scrollTop}px`;
}

export function scrollAble() {
  ableScroll();
}

export function scrollLock() {
  lockScroll();
}
```

### TAB CONTENTS

```sh
export default function tabContent() {

  const tabLinks = document.querySelectorAll('.js-tab-link'),
        tabContents = document.querySelectorAll('.js-tab-content');

  tabLinks.forEach((tabLink) => {
    tabLink.addEventListener('click', (e) => {
      e.preventDefault();

      tabContents.forEach((el) => {
        el.classList.remove(CONST.ACTIVE_CLASS);
      });
      tabLinks.forEach((el) => {
        el.classList.remove(CONST.ACTIVE_CLASS);
      });
      tabLink.classList.add(CONST.ACTIVE_CLASS);

      let target = tabLink.getAttribute('href');
      target = document.querySelector(target);
      target.classList.add(CONST.ACTIVE_CLASS);

    });
  });

}
```

### GET PARENT THROUGH A FUNCTION

```sh
const body = document.querySelector('body')
let current = e.target
let outside = true

while (current && current !== body) {
  if (current.classList.contains('property-location-value')) {
    outside = false
    break
  } else {
    current = current.parentNode
  }
}
```

### GET SECOND CHILD

```sh
el.children[1]
```

### LOADER SESSION

```sh
export default function loaderSession() {
  let loaderEl = document.querySelector('.js-loader');
  let soundEl = document.querySelector('.js-sound');
  if (!sessionStorage.isVisited) {
  sessionStorage.isVisited = 'true'
    loaderEl.style.display = "block";
    soundEl.style.display = "flex";
  } else {
    loaderEl.style.display = "none";
    soundEl.style.display = "none";
  }
}
```

### CALLING  EXPORTS in JS

```sh
export default function myFunction() {

}

// other PROFILE
Usage: import myFunction from './file'

export function myFunction2() {
    ableScroll();
}

Usage: import { myFunction2, myFunction3} from './file'


export const ableScroll = () => {

   $wrap.removeClass(ACTIVE_CLASS);
   $wrap.css({
     'top' : ''
   });
   $headerSide.removeClass(ACTIVE_CLASS);

   $document.scrollTop(scrollTop);
 }
export const lockScroll = () => {
   scrollTop = $document.scrollTop();

   $wrap.addClass(ACTIVE_CLASS);
   $wrap.css({
     'top' : `-${scrollTop}px`
   });
   $headerSide.addClass(ACTIVE_CLASS);

}


export function scrollAble() {
    ableScroll();
}

export function scrollLock() {
    lockScroll();
}

Note: Must separate to export default function …
```

### CALLING EACH in SCROLLMAGIC

```sh
$section.each( (i, e) => {
  let $elem = $(e);
  console.log($elem[0]);

  new ScrollMagic.Scene({
    triggerElement: e,
    triggerHook: CONST.TRIGGER_HOOK
  })
  .reverse(true)
  .setClassToggle($elem[0],CONST.ACTIVE_CLASS)
  .addTo(controller);
} );

or

$animElem.each((i, e) => {
  let $elem = $(e);

  new ScrollMagic.Scene({
    triggerElement: e,
    triggerHook: 'onEnter',
    offset: offset
  })
  .reverse(false)
  .setClassToggle($elem[0],CONST.ACTIVE_CLASS)
  .addTo(controller);
});
```

### ELEMENT IN VIEWPORT

```sh

CONST.$window.on('scroll', function () {
    let $thisWindow = $(this);

    let windowScroll = $thisWindow.scrollTop(),
        windowBottom = windowScroll + CONST.$window.innerHeight();

    const $section = $('.section');

    $section.each( function (i, e) {
      let $this = $(this),
          $elem = $(e);

      let elemTop = $this.position().top,
          elemBottom = elemTop + $this.outerHeight();

      if( ( elemTop >= windowScroll ) && ( elemTop <= windowBottom ||
        elemBottom >= windowBottom && elemTop <= windowScroll ) ) {

        $elem.removeClass(CONST.ACTIVE_CLASS);
        $this.addClass(CONST.ACTIVE_CLASS);

      }
});
```

### INTERSECTION OBSERVER

```sh
let observer = new IntersectionObserver(callback, { rootMargin: '0px 0px -100px 0px' });
       document.querySelectorAll.forEach((section) => {
         observer.observe(section)
       })

       function callback(entries) {
         entries.forEach((entry) => {
           if (entry.isIntersecting) {
             entry.classList.add('is-active');
           }
           else {
             entry.classList.remove('is-active');
           }
         })
       }
```
Example

```sh

let observer = new IntersectionObserver(callback, { rootMargin: '0px 0px -100px 0px' });

 const section = document.querySelectorAll('.js-section');

 section.forEach((sec) => {
   observer.observe(sec);
 })

 function callback(entries) {
   entries.forEach((entry) => {
     if (entry.isIntersecting) {
       let caseAnimationHome = () => {

         const elSlide = entry.target.querySelectorAll('.js-anim-slide');

         elSlide.forEach( (el, i) => {
           delay(i*CONST.DURATION).then(() => {
             el.classList.add(CONST.IS_ACTIVE);

             delay(4*CONST.DURATION).then(() => {
                 const animMoney = entry.target.querySelector(`.js-anim-money`);
                 animMoney.classList.add(CONST.IS_ACTIVE);

                 delay(10*CONST.DURATION).then(() => {
                   const elSlide2 = entry.target.querySelectorAll(`.js-anim-slide-2`);
                   elSlide2.forEach( (el, i) => {
                       delay(i*CONST.DURATION).then(() => {
                         el.classList.add(CONST.IS_ACTIVE);
                       });
                   });
                 });
             });
           });
         });

       }

       if(window.location.pathname === '/'){
         caseAnimationHome();
       }
     }
   })
 }
```
