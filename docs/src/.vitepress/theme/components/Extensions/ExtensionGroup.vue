<script setup lang="ts">
import { toRefs } from 'vue'
import type { Extension } from '../../queries/useExtensionsRepositoryQuery'
import ExtensionItem from './ExtensionItem.vue'

const props = defineProps<{ list: Extension[], totalCount: number }>()
const { list } = toRefs(props)
</script>

<template>
  <div class="extension-group">
    <h2>
      <span>Packages</span>
    </h2>
    <ExtensionItem
      v-for="extension in list"
      :id="extension.pkg"
      :key="extension.apk"
      :item="extension"
    />
  </div>
</template>

<style lang="stylus">
.extension-group h2 {
  display: flex
  align-items: center
  justify-content: space-between

  .extensions-total-sum {
    color: var(--vp-c-brand)
  }
}
</style>
