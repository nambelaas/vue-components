<template>
    <h1>Login</h1>
    <form @submit.prevent="$emit('submit', email, password)">
        <div class="mb-3">
            <input type="email" v-model="email" class="form-control" placeholder="Email">
        </div>
        <div class="mb-3">
            <input type="password" v-model="password" class="form-control" placeholder="Password">
        </div>
        <button type="submit">Login</button>
    </form>
</template>

<script lang="ts">
export default {
    name: "LoginForm",
    data: () =>({
        email: "",
        password: ""
    }),
    emits: {
        submit: (email: String, password: String) => {
            if (email && password) {
                return true
            } else{
                console.warn("Invalid submit event: email and password are required")
                return false
            }
        }
    }
}
</script>