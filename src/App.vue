<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header class="sticky top-0 py-4 lg:py-6">
    <nav class="grid grid-cols-1 gap-x-4 sm:grid-cols-12 text-center">
      <RouterLink to="/" class="rounded hover:bg-blue-300 duration-300">Home</RouterLink>
      <div class="group block relative rounded hover:bg-blue-300 duration-300">
        <a class="block">Tool</a>
        <div
          class="group-hover:scale-y-100 scale-y-0 duration-300 origin-top absolute bg-white divide-y divide-gray rounded border-[#cdcdcd] shadow-[0_1px_6px_#2b2a331a] text-left p-1 min-w-fit"
        >
          <RouterLink to="/tool1" class="block pl-4 pr-1 py-1"
            >Tool1fadfafdasdfarfsdfasdfa</RouterLink
          >
          <RouterLink to="/tool1" class="block pl-4 pr-1 py-1">Tool2</RouterLink>
          <RouterLink to="/tool1" class="block pl-4 pr-1 py-1">Tool2</RouterLink>
          <RouterLink to="/tool1" class="block pl-4 pr-1 py-1">Tool2</RouterLink>
          <RouterLink to="/tool1" class="block pl-4 pr-1 py-1">Tool2</RouterLink>
        </div>
      </div>
    </nav>
  </header>

  <RouterView />
</template>

<style scoped>
/* a {
  display: inline-block;
} */
</style>
