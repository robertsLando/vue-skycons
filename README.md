# Vue Skycons

This was inspired by [Skycons](https://github.com/darkskyapp/skycons) -- a set of ten animated weather glyphs, procedurally generated by JavaScript using the HTML5 canvas tag. They're easy to use, and pretty lightweight, so they shouldn't rain on your parade.

![icons.gif](https://raw.githubusercontent.com/dipu-bd/skycons/master/images/icons.gif)

## Installation

### NPM

```sh
npm install --save vue-skycons
```

### YARN

```sh
yarn add vue-skycons
```

## Examples

### Using Plugin

```js
import Vue from "vue";
import VueSkycons from "vue-skycons";

// Register component
Vue.use(VueSkycons);

// Register component with a default color
Vue.use(VueSkycons, { color: "orangered" });
```

### Using Component

```vue
<template>
  <div>
    <!-- All icons -->
    <skycon condition="clear-day" />
    <skycon condition="clear-night" />
    <skycon condition="partly-cloudy-day" />
    <skycon condition="partly-cloudy-night" />
    <skycon condition="cloudy" />
    <skycon condition="rain" />
    <skycon condition="sleet" />
    <skycon condition="snow" />
    <skycon condition="wind" />
    <skycon condition="fog" />

    <!-- With all attributes -->
    <skycon condition="rain" size="256" />
  </div>
</template>

<script>
import Skycon from "vue-skycons/src/Skycon.vue";

export default {
  components: {
    Skycon
  },
}
```

### Available props

```js
// Weather condition
condition: {
  type: String,
  required: true,
},

// Icon size
size: {
  type: [Number, String],
  default: 64,
},

// Icon color
color: {
  type: String,
  default: "black",
},

// Start with paused animation
paused: {
  type: Boolean,
  default: false,
},
```

### Event example

```vue
<template>
  <skycon condition="snow" size="128" paused @load="onLoad" />
</template>

<script>
export default {
  methods: {
    onLoad(player) {
      console.log("loaded");
      setInterval(() => {
        if (player.paused) {
          player.play();
        } else {
          player.pause();
        }
      }, 1000);
    },
  },
};
</script>
```
