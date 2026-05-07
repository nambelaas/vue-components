<template>
  <div class="mb-3">
    <label class="block mb-2 text-sm font-medium">{{ label }}</label>
    <input v-bind="$attrs" class="border border-gray-300 rounded px-3 py-2 w-full" v-model="value" />
  </div>
</template>

<script lang="ts">
export default {
  name: "BaseInput",
  inheritAttrs: false,
  props: {
    label: {
      type: String,
      required: true,
    },
    modelValue: {
      type: String,
      required: true,
    },
    modelModifiers: {
      type: Object,
      default: () => ({}),
    },
  },
  emits: ["update:modelValue"],
  computed: {
    value: {
      get() {
        return this.modelValue;
      },
      set(value: String) {
        if (this.modelModifiers.lowercase) {
          value = value.toLowerCase();
        }
        this.$emit("update:modelValue", value);
      },
    },
  },
  methods: {
    onInput(event: Event) {
      const target = event.target as HTMLInputElement | null;
      if (target) {
        this.$emit("update:modelValue", target.value);
      }
    },
  },
};
</script>
