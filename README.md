# vue-zoom


## Install / Usage
``` bash
$ npm install vue-zoom
```

```html
<template>
   <div id="app">
      <v-zoom :img="img" :width="width"></v-zoom>
   </div>
</template>

<script>
import vZoom from 'vue-zoom'
export default {
  components: {vZoom},
  data() {
     return {
        img: 'photo.jpg',
        width: 500
     }
  }
}
</script>
```
