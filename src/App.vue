<script lang="ts">
import { ref } from "vue";
import Alert from "./components/Alert.vue";
import Alerts from "./components/Alerts.vue";
import LoginForm from "./components/LoginForm.vue";
import BaseInput from "./components/BaseInput.vue";

// const items = ref(3)
// const show = ref(true)
// const alert = ref({
//   message: "Message",
//   type: ["success", "warning", "danger"]
// })

export default {
  name: "App",
  components: {
    Alert,
    Alerts,
    LoginForm,
    BaseInput,
  },
  data: () => ({
    items: 3,
    show: true,
    alert: {
      message: "Message",
      type: ["success", "warning", "danger"],
    },
    email: "",
    password: "",
  }),
  methods: {
    handleSubmit(email: String, password: String): void {
      alert(email + " " + password);
    },
  },
};
</script>

<template>
  <div class="container py-5 flex flex-col gap-3">
    <!-- <Alert :message="items+' item has been removed'" type="success" :show="true"/> -->
    <!-- <Alert :message="items+' item has been removed'" type="danger" :show="show" @alert-close="show = false" /> -->
    <!-- <Alerts :message="items+' item has been removed'" type="errors" :types="alert.type"/> -->
    <!-- <LoginForm @submit="handleSubmit" /> -->
    <!-- <input
    type="email"
    v-model="email"
    class="form-control"
    placeholder="Email"
    /> -->
    <!-- <BaseInput v-model="email" label="Email" /> -->
    <!-- <BaseInput v-model.lowercase="email" label="Email" /> -->
    <LoginForm
      @submit="handleSubmit"
      v-model:email.lowercase="email"
      v-model:password="password"
    />
    {{ email }} - {{ password }}
  </div>
</template>
