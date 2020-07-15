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

### OBJECT FIT ON IE
```sh
const objectFitPolyfill = function() {

  //  if ('objectFit' in document.documentElement.style === false) {
      Array.prototype.forEach.call(document.querySelectorAll('.js-product-image'), function (image) {
        const div = document.createElement("DIV");
        div.classList.add('product-image-polyfill');
        image.parentNode.appendChild(div);
        image.classList.add('is-hide');
        const imageProp = 'url("' + image.src + '") no-repeat center /' + window.getComputedStyle(image, null).getPropertyValue("object-fit");

        setTimeout(function() {
          image.parentNode.querySelector('.product-image-polyfill').style.background = imageProp;
          image.parentNode.querySelector('.product-image-polyfill').style.width = '100%';
          image.parentNode.querySelector('.product-image-polyfill').style.height = (image.height/2)+'px';
        }, 100);
      });
  //  }

  }

  objectFitPolyfill();
}
```

### FOR SITE IMPROVEMENT AND SPEED

```sh
1. Using of img/svg sprite

References
https://www.toptal.com/developers/css/sprite-generator/
http://www.spritecow.com/
https://spritegen.website-performance.org/
https://css.spritegen.com/

encode to Base64

2. Using of Lazyload

References
https://github.com/tuupola/lazyload
https://wordpress.org/plugins/search/lazy+load


3. font-display property

4. Remove unnecesarry Script by WP
Reference
https://www.denisbouquet.com/remove-wordpress-emoji-code/

5. gzip compress with .htaccess

<ifModule mod_gzip.c>
mod_gzip_on Yes
mod_gzip_dechunk Yes
mod_gzip_item_include file .(html?|txt|css|js|php|pl)$
mod_gzip_item_include handler ^cgi-script$
mod_gzip_item_include mime ^text/.*
mod_gzip_item_include mime ^application/x-javascript.*
mod_gzip_item_exclude mime ^image/.*
mod_gzip_item_exclude rspheader ^Content-Encoding:.*gzip.*
</ifModule>

6. Add async to a part of script

Suggestion
<script async src=""></script>

7. Avoid to load Yugothic
```

### SWITCHING TABS
```sh
function _tabs() {
  const bindAll = function() {
    const menuElements = document.querySelectorAll('.js-tab');
    menuElements.forEach(function(i) {
      i.addEventListener('click', change, false);
    });
  }

  const clear = function() {
    var menuElements = document.querySelectorAll('.js-tab');
    menuElements.forEach(function(i) {
      i.classList.remove('is-active');
      const id = i.getAttribute('data-tab');
      document.getElementById(id).classList.remove('is-active');
      localStorage.removeItem('currentTab');
    });
  }

  const change = function(e) {
    e.preventDefault();
    clear();
    e.target.classList.add('is-active');
    const id = e.currentTarget.getAttribute('data-tab');
    localStorage.setItem("currentTab", id);
    document.getElementById(id).classList.add('is-active');
  }

  let currentTabSelected = localStorage.getItem('currentTab');
  if(currentTabSelected !== null) {
    clear();
    document.getElementById(currentTabSelected).classList.add('is-active');
    document.querySelector('.js-tab[data-tab='+currentTabSelected+']').classList.add('is-active');
  } else {
    document.getElementById('content-new').classList.add('is-active');
    document.querySelector('.js-tab[data-tab=content-new]').classList.add('is-active');
  }

  bindAll();
}
```

### IPAD SCALE
```sh
function _iPadView() {
const ua = navigator.userAgent
const sp = (ua.indexOf('iPhone') > 0 || ua.indexOf('Android') > 0 && ua.indexOf('Mobile') > 0);
const tab = (ua.indexOf('iPad') > 0 || (!sp && ua.indexOf('Android') > 0));
const isIOS = /iPad/.test(navigator.platform) || (navigator.platform === 'MacIntel' && navigator.maxTouchPoints > 1);
const checkVersion = /Version\/13/;
let ipadScale = window.screen.width / 1100;

if(isIOS && checkVersion.test(navigator.userAgent) || tab) {
  document.querySelector('meta[name="viewport"]').setAttribute('content', 'width=device-width,initial-scale='+ipadScale+',maximum-scale='+ipadScale+',user-scalable=0');
}
}
```

### DEVICE HACK
```sh
function _deviceCheck() {
const $body = document.querySelector('html'),
      userAgent = navigator.userAgent;
let classBrowser = null,
    classOS = null;

const getBrowser = function() {
  let browser = null;

  if ((navigator.userAgent.indexOf("Opera") || navigator.userAgent.indexOf('OPR')) !== -1) {
    browser = 'is-opera';
  } else if (navigator.userAgent.indexOf("Edge") >= 0) {
    browser = 'is-edge';
  } else if (navigator.userAgent.indexOf("Chrome") !== -1) {
    browser = 'is-chrome';
  } else if (navigator.userAgent.indexOf("Safari") !== -1) {
    browser = 'is-safari';
  } else if (navigator.userAgent.indexOf("Firefox") !== -1) {
    browser = 'is-firefox';
  } else if ((navigator.userAgent.indexOf("MSIE") !== -1) || (!!document.documentMode === true)) {
    browser = 'is-ie';
  }

  return browser;
}
```

### BROWSER HACK
```sh
const getOS = function() {
  const platform = window.navigator.platform,
        macosPlatforms = ['Macintosh', 'MacIntel', 'MacPPC', 'Mac68K'],
        windowsPlatforms = ['Win32', 'Win64', 'Windows', 'WinCE'],
        iosPlatforms = ['iPhone', 'iPad', 'iPod'];
  let os = null;

  if (macosPlatforms.indexOf(platform) !== -1) {
    os = 'is-mac';
  } else if (iosPlatforms.indexOf(platform) !== -1) {
    os = 'is-ios';
  } else if (windowsPlatforms.indexOf(platform) !== -1) {
    os = 'is-windows';
  } else if (/Android/.test(userAgent)) {
    os = 'is-android';
  } else if (!os && /Linux/.test(platform)) {
    os = 'is-linux';
  }

  return os;
}

classBrowser = getBrowser();
classOS = getOS();
$body.classList.add(classBrowser, classOS);
}
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

### LAZYLOAD

```sh
import 'intersection-observer';

export default function Lazyload() {
  let observer = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting && !e.target.classList.contains('loaded')) {
        let el = e.target;

        if (el.dataset.src && (el.nodeName.toLowerCase() === 'img')) {
          el.setAttribute('src', el.dataset.src);
        } else {
          el.style.backgroundImage = "url("+el.dataset.src+")";
        }

        e.target.classList.add('loaded');
      }
    });
  }, {
      rootMargin: (window.innerWidth <= 767) ? `${window.innerHeight * 2}px 0px ${window.innerHeight * 2}px 0px` : '0px 0px 0px 0px'
  });

  const lazyload = document.querySelectorAll('.lazyload');
  lazyload.forEach(img => {
    observer.observe(img);
  });
}

for images src, create pixel image
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

```sh
const button = document.querySelector('.js-scroll-button');

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

FOREACH

```sh
const buttons = document.querySelectorAll('.js-scroll-button');
buttons.forEach( button => {
  button.addEventListener('click', e => {
    e.preventDefault();
    const hash = e.currentTarget.getAttribute('href');
    const yCoordinate = document.querySelector(hash).getBoundingClientRect().top + window.pageYOffset;

    window.scrollTo({
        top: yCoordinate,
        behavior: 'smooth'
    });
  });
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
