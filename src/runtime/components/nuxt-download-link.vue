<template>
  <a :key="nSrc" :target="target" :download="download" :href="nSrc">
    <slot>{{ nSrc }}</slot>
  </a>
</template>

<script lang="ts">
import { imageMixin } from './image.mixin'

export default {
  name: 'NuxtDownloadLink',
  mixins: [imageMixin],
  props: {
    download: { type: Boolean, default: false },
    newWindow: { type: Boolean, default: true }
  },
  computed: {
    nSrc (): string {
      return this.$img(this.src, this.nModifiers, this.nOptions)
    },
    target (): string | boolean {
      return this.newWindow ? '_blank' : false
    }
  }
}
</script>
