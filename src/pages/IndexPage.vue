<template>
  <q-page class="flex flex-center">
    <ImageRandomizer v-if="userLogged"></ImageRandomizer>
    <LoginForm v-else @callback-login="() => setUserLogged()"></LoginForm>
  </q-page>
</template>

<script setup>
import ImageRandomizer from "../components/ImageRandomizer.vue";
import LoginForm from "../components/LoginForm.vue";
import { ref } from "vue";

const userLogged = ref(false);

const setUserLogged = () => {
  userLogged.value = true;
};

defineOptions({
  name: "IndexPage",
});
</script>
