<template>
  <div
    class="modal w-full fixed inset-0 z-50 flex items-center justify-center"
    tabindex="-1"
    v-show="show"
  >
    <div
      class="modal-dialog w-md mx-auto rounded-lg border border-gray-300 bg-white"
    >
      <div class="modal-content p-4 flex flex-col gap-4">
        <div class="modal-header flex-none border-b border-gray-300 pb-3">
          <slot name="header">Default Header Text</slot>
        </div>
        <div class="modal-body grow border-b border-gray-300 pb-3">
          <slot>Default Body Text</slot>
        </div>
        <div class="modal-footer flex-none">
          <slot name="footer">Default Footer Text</slot>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: "Modal",
  props: {
    show: {
      type: Boolean,
      default: true,
    },
  },
};
</script>
