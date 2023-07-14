<script setup lang="ts">
interface Props {
  header: any;
  info: any;
}

defineProps<Props>()
</script>

<template>
  <li v-if="info !== ''">{{ header }} : {{ info }}</li>
</template>
