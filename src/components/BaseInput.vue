<template>
  <div class="mb-3">
    <label class="form-label mb-2">{{ label }}</label>
    <input type="text" class="form-control" v-model="value" />
  </div>
</template>

<script lang="ts">
export default {
  name: "BaseInput",
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
