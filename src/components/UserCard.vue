<script setup lang="ts">

interface Props {
  user: any;
}

defineProps<Props>()

</script>

<template>
  <ul>
    <li>
      {{user.name}} : <img :src="user.avatar_url" :alt="user.login" />
    </li>
    <li>
      {{user.location}}
    </li>
  </ul>
</template>

<style scoped>

</style>
