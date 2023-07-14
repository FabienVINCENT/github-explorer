<script setup lang="ts">
import {ref} from "vue";
import {useThrottleFn, useFetch} from "@vueuse/core";

export interface User {
  login: string;
  name: string;
  id: number;
  node_id: string;
  avatar_url: string;
  gravatar_id: string;
  url: string;
  html_url: string;
  followers_url: string;
  following_url: string;
  gists_url: string;
  starred_url: string;
  subscriptions_url: string;
  organizations_url: string;
  repos_url: string;
  events_url: string;
  received_events_url: string;
  type: string;
  site_admin: boolean;
  hireable: boolean;
  location: string;
  twitter_username: string;
  bio: string;
  blog: string;
  email: string;
  company: string;
  following: number;
  followers: number;
  public_repos: number;
  public_gists: number;
  created_at: string;
}

const username = ref('')
const results = ref<User[]>([])

const searchUser = async () => {
  if (!username.value) {
    results.value = []
    return
  }
  const url = `https://api.github.com/search/users?q=${username.value}`
  const {data}: any = await (useFetch(url).json())
  results.value = data.value.items
}

// Debounde searchUser
const debounceSearchUser = useThrottleFn(searchUser, 500)

const emit = defineEmits<{
  select: [username: string]
}>()

const handleUsername = (username: string) => {
  console.log(username)
  results.value = []
  emit('select', username)
}

</script>

<template>
  <div>
    <input v-model="username" @input="debounceSearchUser" />
    <div>
      <ul>
        <li v-for="result in results" :key="result.id" @click="handleUsername(result.login)">{{result.login}}</li>
      </ul>
    </div>
  </div>
</template>

<style scoped>

</style>
