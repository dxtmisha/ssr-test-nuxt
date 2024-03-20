<script setup lang="ts">
const {data} = await useAsyncData<{ data: { title: string, description: string } }>(
    'vukhtantu',
    () => $fetch('https://symfony.f56go.com/vukhtantu/description')
)

const title = computed(() => data.value && data.value.data.title)
const description = computed(() => data.value && data.value.data.description)
</script>

<template>
  <div class="v-description__return">
    <NuxtLink to="/">return</NuxtLink>
  </div>
  <div v-if="data">
    <h1>{{ title }}</h1>
    <div v-html="description"></div>
  </div>
</template>

<style scoped>
.v-description__return {
  padding-bottom: 16px;
}
</style>
