<template>
  <div class="q-pa-md" style="max-width: 400px">
    <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
      <q-input
        filled
        v-model="username"
        label="Seu usuário"
        hint="Digite o seu usuário"
        lazy-rules
        :rules="[
          (val) => (val && val.length > 0) || 'Por favor, digite seu usuário',
        ]"
      />

      <q-input
        filled
        type="password"
        v-model="password"
        label="Sua senha"
        lazy-rules
        :rules="[
          (val) => (val !== null && val !== '') || 'Por favor digite sua senha',
        ]"
      />

      <div>
        <q-btn label="Acessar" type="submit" color="primary" />
        <q-btn
          label="Reiniciar"
          type="reset"
          color="primary"
          flat
          class="q-ml-sm"
        />
      </div>
    </q-form>
  </div>
</template>

<script>
import { useQuasar } from "quasar";
import { ref } from "vue";
import axios from "axios";

export default {
  setup(props, context) {
    const $q = useQuasar();

    const username = ref(null);
    const password = ref(null);
    const isLogged = ref(false);

    return {
      username,
      password,
      isLogged,
      async onSubmit() {
        const userisValid = await axios.post(
          "https://rarysonpere-api-dos-vei-15.deno.dev/login",
          { username: username.value, password: password.value }
        );
        if (!userisValid.data) {
          $q.notify({
            color: "red-4",
            textColor: "white",
            message: "Dados incorretos",
          });
        } else {
          isLogged.value = true;
          context.emit("callback-login");
          $q.notify({
            color: "green-4",
            textColor: "white",
            message: "Login feito com sucesso",
          });
        }
      },

      onReset() {
        username.value = null;
        password.value = null;
      },
    };
  },
};
</script>
