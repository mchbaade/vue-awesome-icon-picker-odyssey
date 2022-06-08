# VueMaterialDesignIconPicker

A Vue.js icon picker component to easily pick a MaterialDesignIcon & use it.

![print screen](docs/img/btn.PNG)

![print screen](docs/img/main.PNG)

## Table of contents

- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
    - [Options](#options)
- [Events](#events)

## Installation

Install using `npm`   

```
npm install --save vue-material-design-icon-picker
```

OR use it via `cdn`   

```html
<script src="https://unpkg.com/vue-material-design-icon-picker@1.0.0/dist/vue-material-design-icon-picker.min.js"></script>
```

Then Register The Component Globally:

```javascript
import Vue from 'vue';
import VueMaterialDesignIconPicker from 'vue-material-design-icon-picker';

Vue.component('vue-material-design-icon-picker', VueMaterialDesignIconPicker)
```

OR use it in a Component:

```javascript
import VueMaterialDesignIconPicker from 'vue-material-design-icon-picker';

export default {
    name: 'YourMaterialDesignComponent',
    components: {
        'vue-material-design-icon-picker': VueMaterialDesignIconPicker
    },
}
```


## Usage

Use it like:

```html
<vue-material-design-icon-picker />
```


## Configuration

You can also pass Options as props in the `vue-material-design-icon-picker` component as you can see the example below

```html
<vue-material-design-icon-picker :icon-preview="false" :colorMdi="32C3BC" :iconPlaceholder="bone-off" />
```
Remember that all options are optional and you can check the default values below:

### Options

```javascript
/**
 * The Text which will be shown to the Select Icon Button
 */
button: {
    type: String,
    default: 'Escolha um ícone'
},
/**
 * Header Title
 */
title: {
    type: String,
    default: 'Escolha um ícone'
},
/**
 * Whether the Icon should displayed or not
 */
iconPreview: {
    type: Boolean,
    default: true
}
```

## Events

VueMaterialDesignIconPicker will emit a `selected(icon)` event when user selects an icon.

```html
<vue-material-design-icon-picker @selected="onIconSelected" />
```

```javascript
{
    methods: {
        onIconSelected(icon) {
            // your code here
        }
    }
}
```
