<script setup lang="ts">
import { ref } from 'vue'
import Alert from './components/Alert.vue';
import Alerts from './components/Alerts.vue';

const items = ref(3)
const show = ref(true)
const alert = ref({
  message: "Message",
  type: ["success", "warning", "danger"]
})

</script>

<template>
  <!-- <Alert :message="items+' item has been removed'" type="success" :show="true"/> -->
  <Alert :message="items+' item has been removed'" type="danger" />
  <!-- <Alerts :message="items+' item has been removed'" type="errors" :types="alert.type"/> -->
</template>
