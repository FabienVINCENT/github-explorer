<script setup lang="ts">
import UserCard from "@/components/UserCard/UserCard.vue";
import SearchUser from "@/components/SearchUser.vue";
import {ref} from "vue";

const username = ref('')

const handleSelect = (usernameSelected: string) => {
  username.value = usernameSelected
}
</script>

<template>
  <div>
    <search-user @select="handleSelect"/>
    <user-card v-if="username" :username="username" />
  </div>
</template>

