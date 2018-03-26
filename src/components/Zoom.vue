<template>
    <div class="zoom">
        <img :src="img" :width="width">
    </div>
</template>

<script lang="babel">
window.jQuery = require('jquery');
window.$ = window.jQuery;

require('jquery-zoom');

export default {
    props:{
        /**
         * The image to display
         * @type {String}
         */
      img: {
          type: String,
          required: true
      },
        /**
         * The width of the image
         * @type {String||Number}
         */
      width: {
          type: [String, Number],
          required: true
      },
        /**
         * The url of the large photo to be displayed. If no url is provided, zoom uses the src of the first child
         * IMG element inside the element it is assigned to.
         * @type {String||Boolean}
         */
      url: {
          type: [String, Boolean],
          default: false
      },
        /**
         * The type of event that triggers zooming. Choose from mouseover, grab, click, or toggle.
         * @type {String}
         */
      on: {
          type: String,
          default: 'mouseover'
      },
        /**
         * The fadeIn/fadeOut speed of the large image.
         * @type {String||Number}
         */
      duration: {
          type: [String, Number],
          default: 120
      },
        /**
         * A selector or DOM element that should be used as the parent container for the zoomed image.
         * @type {String||Boolean}
         */
      target: {
          type: [String, Boolean],
          default: false
      },
        /**
         * Enables interaction via touch events.
         * @type {Boolean}
         */
      touch: {
          type: Boolean,
          default: true
      },
        /**
         * This value is multiplied against the full size of the zoomed image.
         * The default value is 1, meaning the zoomed image should be at 100% of its natural width and height.
         * @type {String||Number}
         */
      magnify: {
          type: [String, Number],
          default: 1
      },
        /**
         * A function to be called when the image has loaded. Inside the function, `this` references the image element.
         * @type {Function||Boolean}
         */
      callback: {
          type: [Function, Boolean],
          default: false
      },
        /**
         * A function to be called when the image has zoomed in. Inside the function, `this` references the image element.
         * @type {Function||Boolean}
         */
      onZoomIn: {
          type: [Function, Boolean],
          default: false
      },
        /**
         * A function to be called when the image has zoomed out. Inside the function, `this` references the image element.
         * @type {Function||Boolean}
         */
      onZoomOut: {
          type: [Function, Boolean],
          default: false
      }
    },
    mounted () {
        $(this.$el).zoom({
            url: this.url,
            on: this.on,
            duration: this.duration,
            target: this.target,
            touch: this.touch,
            magnify: this.magnify,
            callback: this.callback,
            onZoomIn: this.onZoomIn,
            onZoomOut: this.onZoomOut
        });
    }
}
</script>

<style>
    .zoom {
      display: inline-block;
      position: relative;
      }

    .zoom:after {
      content: '';
      display: block;
      width: 33px;
      height: 33px;
      position: absolute;
      top: 0;
      right: 0;
      background: url(https://raw.github.com/jackmoore/zoom/master/icon.png);
      }

    .zoom img {
      display: block;
      }

    .zoom img::-moz-selection {
      background-color: transparent;
      }

    .zoom img::selection {
      background-color: transparent;
      }
</style>
