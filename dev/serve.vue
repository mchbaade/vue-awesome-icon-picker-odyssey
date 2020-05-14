<script>
import Vue from 'vue';
import VueAwesomeIconPicker from '@/vue-awesome-icon-picker.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    VueAwesomeIconPicker
  }
});
</script>

<template>
  <div id="app">
    <vue-awesome-icon-picker />
  </div>
</template>
