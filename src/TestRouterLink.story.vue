<script setup lang="ts">
import { AfLinkPrimary } from '@af-lib/ui-lib'
import { ref } from 'vue'
import { createRouter, createMemoryHistory } from 'vue-router'

import type { App } from 'vue'

const label = ref<string>('ZeldaLinkToThePast')
const to = ref('/')
const size = ref<'sm' | 'md' | 'lg'>('md')
const showIcon = ref(false)
const showArrow = ref(false)
const disabled = ref(false)

const sizeOptions = ['sm', 'md', 'lg']

function setupApp({ app }: { app: App }) {
  // Router mock
  app.use(
    createRouter({
      history: createMemoryHistory(),
      routes: [{ path: '/', name: 'home', component: { render: () => null } }],
    })
  )
}
</script>

<template>
  <Story
    title="Atoms/AfLink/AfLinkPrimary"
    auto-props-disabled
    :setup-app="setupApp"
  >
    <router-link to="/"> Hello </router-link>

    <template #controls>
      <HstText v-model="label" title="Label" />
      <HstText v-model="to" title="To" />
      <HstSelect v-model="size" :options="sizeOptions" title="Size" />
      <HstCheckbox v-model="showIcon" title="Show icon" />
      <HstCheckbox v-model="showArrow" title="Show arrow" />
      <HstCheckbox v-model="disabled" title="Disabled" />
    </template>
  </Story>
</template>

<style scoped></style>
