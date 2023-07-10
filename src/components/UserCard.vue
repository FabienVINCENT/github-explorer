<script setup lang="ts">
import type {UserType} from "@/components/AsyncHome.vue";

interface Props {
  user: UserType;
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
