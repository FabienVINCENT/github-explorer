<script setup lang="ts">

import AsyncHome from "@/components/AsyncHome.vue";
</script>

<template>
  <main>
    <suspense>
      <template #default>
        <async-home />
      </template>
      <template #fallback>
        <div>Loading...</div>
      </template>
    </suspense>
  </main>
</template>

