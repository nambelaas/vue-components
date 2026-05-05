<script lang="ts">
import { ref } from 'vue'
import Alert from './components/Alert.vue';
import Alerts from './components/Alerts.vue';
import LoginForm from './components/LoginForm.vue';

// const items = ref(3)
// const show = ref(true)
// const alert = ref({
//   message: "Message",
//   type: ["success", "warning", "danger"]
// })

export default {
  name: 'App',
  components: {
    Alert,
    Alerts,
    LoginForm
  },
  props:{
    items: {
      type: Number,
      default: 0
    },
    show:{
      type: Boolean,
      default: true
    },
    alert: {
      type: Object,
      default: () => ({
        message: "Message",
        type: ["success", "warning", "danger"]
      })
    }
  },
  methods:{
    handleSubmit(email: String, password: String): void{
      alert(email + " " + password)
    }
  }
}

</script>

<template>
  <!-- <Alert :message="items+' item has been removed'" type="success" :show="true"/> -->
  <!-- <Alert :message="items+' item has been removed'" type="danger" :show="show" @alert-close="show = false" /> -->
  <!-- <Alerts :message="items+' item has been removed'" type="errors" :types="alert.type"/> -->
   <LoginForm @submit="handleSubmit" />

</template>
