# vue-cardswipe

[![npm](https://img.shields.io/npm/v/vue-cardswipe.svg)](https://www.npmjs.com/package/vue-cardswipe)
[![vue2](https://img.shields.io/badge/vue-2.x-brightgreen.svg)](https://vuejs.org/)

A Vue plugin for reading credit card data from magnetic swipe readers.

This plugin is a port from  the [CarlRaymond/jquery.cardswipe](https://github.com/CarlRaymond/jquery.cardswipe). Please view the repo for more detailed documentation.

[CardSwipe Demo](https://wuori.github.io/vue-cardswipe/example/)

Note: Demo requires a magnetic card reader to use.

## Installation

```sh
yarn add vue-cardswipe
- OR -
npm install vue-cardswipe
```

## Using this plugin

Adding vue-cardswipe to your application requires a few additional steps vs. other Vue plugins as it requires (at the very minimum) a `success` callback.

```js
import Vue from 'vue';

import VueCardSwipe from 'vue-cardswipe';

Vue.use(VueCardSwipe);

new Vue({
  el: '#app',
  ...
  methods{
    handleSwipeSuccess(cardData){
        this.number = cardData.account;
        this.expiry = cardData.expMonth + '/' + cardData.expYear.slice(-2);  
    },
    cardSwipeInit: function(){
      this.$cardSwipe.init({
        success: this.handleSwipeSuccess
      });
    },
  },
  mounted(){
    this.cardSwipeInit();
  }
});
```

After installing, when you component is mounted a document listener for credit card input is added, then any resulting data is sent to your `success` callback.

View the [advanced example](https://wuori.github.io/vue-cardswipe/example/) to see a working implementation.

## Credits

This plugin was originally a clone of [CarlRaymond/jquery.cardswipe](https://github.com/CarlRaymond/jquery.cardswipe). This instance simply ports the functionalities into a Vue plugin.

## :copyright: License

[MIT](http://opensource.org/licenses/MIT)
