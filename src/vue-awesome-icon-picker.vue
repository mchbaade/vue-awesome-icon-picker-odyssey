<template>
  <div class="rbt-icon-picker">
        <span class="icon-preview" v-if="iconPreview && selectedIcon">
            <i :class="`${selectedIcon[0]} fa-${selectedIcon[1]}`"></i>
        </span>
    <button @click="popUpActive = true" class="picker-btn">
      {{ button }}
    </button>

    <div class="rip-popup-component" :style="popupActiveStyle">
      <div class="rip-popup-bg"></div>
      <div class="rip-popup">
        <header class="rip-popup-header">
          <h3>{{ title }}</h3>
          <span @click="popUpActive = false">&times;</span>
        </header>

        <div class="rip-popup-content">
          <div class="rip-search">
            <div class="rip-input">
              <label for="ripSearch" style="display: none;">Search for Icon</label>
              <input id="ripSearch" placeholder="Search for Icon" v-model="searchValue"/>
              <span class="input-append">
                            <i class="fas fa-search"></i>
                        </span>
            </div>
          </div>

          <div class="rip-content">
            <ul class="rip-row">
              <li v-for="(icon, index) in viewableIcons" :key="index" class="rip-col">
                <div class="icon-content text-center">
                  <div class="icon-el" @click="selectIcon(icon)">
                    <!--<font-awesome-icon :icon="icon" />-->
                    <i :class="`${icon[0]} fa-${icon[1]}`"></i>
                  </div>
                  <div class="icon-title">
                    {{ icon[1] }}
                  </div>
                </div>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import ripIcons from './assets/icons.json';
  import('@fortawesome/fontawesome-free/js/all');

  export default {
    name: 'VueAwesomeIconPicker',
    props: {
      button: {
        type: String,
        default: 'Pick A Icon'
      },
      title: {
        type: String,
        default: 'Vue Awesome Icon Picker'
      },
      iconPreview: {
        type: Boolean,
        default: true
      }
    },
    data() {
      return {
        loading: false,
        allIcons: [],
        resultIcons: [],

        popUpActive: false,
        selectedIcon: '',
        searchValue: ''
      }
    },
    methods: {
      selectIcon(icon) {
        this.selectedIcon = icon;
        this.popUpActive = false;
        this.$emit('selected', icon);
      }
    },
    created() {
      Object.keys(ripIcons).forEach(key => {
        let i = ripIcons[key].split(' ');
        this.allIcons.push([i[0], i[1].substr(3)]);
      });
    },
    computed: {
      popupActiveStyle() {
        return !this.popUpActive ? 'display: none;' : '';
      },
      viewableIcons() {
        return this.resultIcons && this.resultIcons.length > 0
                ? this.resultIcons
                : this.allIcons;
      }
    },
    watch: {
      'searchValue': function (val) {
        if(!val) {
          this.resultIcons = [];
        } else {
          this.resultIcons = this.allIcons.filter(icon => icon[1].search(val.toLowerCase()) >= 0)
        }
      }
    }
  };
</script>

<style lang="scss" scoped>
  @import "./assets/RbtIconPicker";
</style>
