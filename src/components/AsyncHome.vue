<script setup lang="ts">
import { Octokit} from "octokit";
import {onMounted, ref} from "vue";
import UserCard from "@/components/UserCard.vue";
import type {GetResponseDataTypeFromEndpointMethod} from "@octokit/types";

export type UserType = GetResponseDataTypeFromEndpointMethod<
    typeof octokit.rest.users.getByUsername
>;

const octokit = new Octokit({});

const getData = async () => {
  return await octokit.rest.users.getByUsername({
    username: "FabienVINCENT",
  });
};

const dataUser = ref<UserType|null>(null);


onMounted(async () => {
  const toto = (await getData()).data;

  dataUser.value = toto;
});

</script>

<template>
  <div v-if="dataUser">
    <user-card :user="dataUser" />
  </div>
</template>

