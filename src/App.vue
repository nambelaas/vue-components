<script lang="ts">
import { ref } from "vue";
import Alert from "./components/Alert.vue";
import Alerts from "./components/Alerts.vue";
import LoginForm from "./components/LoginForm.vue";
import BaseInput from "./components/BaseInput.vue";
import BaseButton from "./components/BaseButton.vue";
import Modals from "./components/Modal.vue";

export default {
  name: "App",
  components: {
    Alert,
    Alerts,
    LoginForm,
    BaseInput,
    BaseButton,
    Modals,
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
    message: "Alert Message",
  }),
  methods: {
    handleSubmit(email: String, password: String): void {
      alert(email + " " + password);
    },
  },
};
</script>

<template>
  <div class="flex flex-col gap-3">
    <!-- <Alert :message="items+' item has been removed'" type="success" :show="true"/> -->
    <!-- <Alert type="danger" :show="show" @alert-close="show = false">
      <span>{{ message }}</span>
    </Alert> -->
    <!-- <Alerts :message="items+' item has been removed'" type="errors" :types="alert.type"/> -->
    <!-- <LoginForm @submit="handleSubmit" /> -->
    <!-- <input
    type="email"
    v-model="email"
    class="border border-gray-300 rounded px-3 py-2 w-full"
    placeholder="Email"
    /> -->
    <!-- <BaseInput v-model="email" label="Email" /> -->
    <!-- <BaseInput v-model.lowercase="email" label="Email" type="email" /> -->
    <!-- <LoginForm
      @submit="handleSubmit"
      v-model:email.lowercase="email"
      v-model:password="password"
    /> -->
    <!-- <BaseButton
      text="Submit"
      theme="primary"
      @click="show = true"
      class="mt-3"
      id="test"
    /> -->
    <!-- {{ email }} - {{ password }} -->
    <Alert
      type="success"
      :show="show"
      @alert-close="show = false"
      v-slot="scopedSlot"
    >
      <span
        >{{ message }}
        <a href="#" :class="scopedSlot.alertLink">Alert Link!</a></span
      >
    </Alert>
  </div>
  <!-- <Modals :show="show">
    <template #header><h2 class="text-lg font-bold">Hii</h2></template>
    <p>Welcome to the page</p>
    <template #footer>
      <BaseButton text="Submit" @click="show = false" />
    </template>
  </Modals> -->
</template>
