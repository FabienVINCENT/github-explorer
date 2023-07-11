<script setup lang="ts">
import UserCard from "@/components/UserCard.vue";
import {useFetch} from "@vueuse/core";


const url = 'https://api.github.com/users/FabienVINCENT'
const { isFetching, data } = await (useFetch(url).json())
</script>

<template>
  <div v-if="!isFetching">
    <user-card :user="data" />
  </div>
</template>

