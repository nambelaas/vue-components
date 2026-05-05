<script lang="ts">
import Alert from './Alert.vue';

export default{
    name:"Alerts",
    components:{
        Alert
    },
    props:{
        message:{
            type: String,
            required: true
        },
        type:{
            type: String,
            default: "success"
        },
        types:{
            type: Array as () => string[],
            default: () => ["success"]
        }
    }
}
</script>

<template>
    <Alert :message="message" :type="type" v-for="type in types" :key="type" :show="true" />
</template>