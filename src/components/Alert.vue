<template>
  <div :class="['alert', 'alert-' + type, 'alert-dismissable']" v-show="show">
    <slot :alertLink="alertLink">Default Message</slot>
    <button type="button" @click="close" class="btn-close">&times;</button>
  </div>
</template>

<script lang="ts">
export default {
  name: "Alert",
  props: {
    type: {
      type: String,
      default: "success",
      validator: function (value: string) {
        return ["success", "warning", "danger"].includes(value);
      },
    },
    // message:{
    //     type: String,
    //     required: true
    // },
    show: {
      type: Boolean,
      default: true,
    },
  },
  methods: {
    close() {
      this.$emit("alertClose");
    },
  },
  emits: ["alertClose"],
  data: () => ({
    alertLink: "alert-link",
  }),
};
</script>
