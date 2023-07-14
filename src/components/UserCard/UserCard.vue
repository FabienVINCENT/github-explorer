<script setup lang="ts">

import UserCardItem from "@/components/UserCard/UserCardItem.vue";
import type {User} from "@/components/SearchUser.vue";
import {computed, } from "vue";
import {useFetch} from "@vueuse/core";

interface Props {
  username: string;
}

const props = defineProps<Props>()

const user = computed<User>(() => data.value)

const url = computed(() => `https://api.github.com/users/${props.username}`)
const {isFetching, data} = await (useFetch(url, {refetch: true}).json())
</script>

<template>
  <div v-if="!isFetching && user">
    <img :src="user.avatar_url" :alt="user.login"/>
    <ul>
      <user-card-item header="Name" :info="user.name"/>
      <user-card-item header="Created at" :info="user.created_at"/>
      <user-card-item header="Bio" :info="user.bio"/>
      <user-card-item header="Public repos" :info="user.public_repos"/>
      <user-card-item header="Public gists" :info="user.public_gists"/>
      <user-card-item header="followers" :info="user.followers"/>
      <user-card-item header="following" :info="user.following"/>
      <user-card-item header="Company" :info="user.company"/>
      <user-card-item header="email" :info="user.email"/>
      <user-card-item header="Hireable" :info="user.hireable"/>
      <user-card-item header="Blog" :info="user.blog"/>
      <user-card-item header="Location" :info="user.location"/>
      <user-card-item header="Twitter" :info="user.twitter_username"/>
      <user-card-item header="Lien profile" :info="user.html_url"/>
      <user-card-item header="Gists url" :info="user.gists_url"/>
      <user-card-item header="Starred url" :info="user.starred_url"/>
      <user-card-item header="Subscriptions url" :info="user.subscriptions_url"/>
      <user-card-item header="Organizations url" :info="user.organizations_url"/>
      <user-card-item header="Repo url" :info="user.repos_url"/>
      <user-card-item header="events url" :info="user.events_url"/>
      <user-card-item header="received_events_url url" :info="user.received_events_url"/>
    </ul>
  </div>
</template>

<style scoped>

</style>
