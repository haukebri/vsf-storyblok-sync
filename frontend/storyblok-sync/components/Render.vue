<template>
  <div class="container" v-editable="item">
    <component v-if="component" :is="component" :item="item" />
  </div>
</template>

<script>
import Vue from 'vue'
export default Vue.extend({
  name: 'SbRender',
  computed: {
    component: function () {
      return this.components[this.item.component] || this.components.debug
    },
    components: function () {
      return {
        debug: () => import('./Debug.vue')
      }
    }
  },
  props: {
    item: {
      type: Object,
      required: true
    }
  }
})
</script>
