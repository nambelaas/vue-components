<template>
  <h1>Login</h1>
  <form @submit.prevent="$emit('submit', email, password)">
    <div class="mb-3">
      <!-- <input type="email" v-model="email" class="form-control" placeholder="Email"> -->
      <input
        type="email"
        :value="email"
        @input="inputEmail"
        class="border border-gray-300 rounded px-3 py-2 w-full"
        placeholder="Email"
      />
    </div>
    <div class="w-full mb-3">
      <!-- <input
        type="password"
        v-model="password"
        class="form-control"
        placeholder="Password"
      /> -->
      <input
        type="password"
        :value="password"
        @input="inputPassword"
        class="border border-gray-300 rounded px-3 py-2 w-full"
        placeholder="Password"
      />
    </div>
    <button type="submit" class="px-4 py-2 bg-blue-500 text-white rounded-md">
      Login
    </button>
  </form>
</template>

<script lang="ts">
export default {
  name: "LoginForm",
  props: {
    email: {
      type: String,
      default: "",
    },
    emailModifiers: {
      type: Object,
      default: () => ({}),
    },
    password: {
      type: String,
      default: "",
    },
  },
  // data: () =>({
  //     email: "",
  //     password: ""
  // }),
  emits: {
    submit: (email: String, password: String) => {
      if (email && password) {
        return true;
      } else {
        console.warn("Invalid submit event: email and password are required");
        return false;
      }
    },
    "update:email": null,
    "update:password": null,
  },
  methods: {
    inputEmail(event: Event) {
      const target = event.target as HTMLInputElement | null;
      if (target) {
        if (this.emailModifiers.lowercase) {
          this.$emit("update:email", target.value.toLowerCase());
        } else {
          this.$emit("update:email", target.value);
        }
      }
    },
    inputPassword(event: Event) {
      const target = event.target as HTMLInputElement | null;
      if (target) {
        this.$emit("update:password", target.value);
      }
    },
  },
};
</script>
