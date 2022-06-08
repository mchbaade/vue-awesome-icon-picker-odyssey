<script>
import Vue from 'vue';
import VueMaterialDesignIconPicker from '@/vue-material-design-icon-picker.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    VueMaterialDesignIconPicker
  }
});
</script>

<template>
  <div id="app">
    <vue-material-design-icon-picker />
  </div>
</template>
