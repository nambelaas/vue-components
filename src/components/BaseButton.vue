<template>
  <button :class="['btn', 'btn-' + theme]">{{ text }}</button>
</template>

<script lang="ts">
export default {
  name: "BaseButton",
  created() {
    console.log(this.$attrs);
  },
  props: {
    class: String,
    id: String,
    text: {
      type: String,
      required: true,
    },
    theme: {
      type: String,
      default: "primary",
      validator: function (value: string) {
        return [
          "primary",
          "secondary",
          "success",
          "danger",
          "warning",
          "info",
        ].includes(value);
      },
    },
  },
};
</script>
