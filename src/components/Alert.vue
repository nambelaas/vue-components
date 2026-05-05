<template>
    <div :class="['alert','alert-'+type]" v-show="show">
        {{ message }}
    </div>
</template>

<script lang="ts">
export default{
    name:"Alert",
    props:{
        type:{
            type:String,
            default:"success"
        },
        message:{
            type: String,
            required: true
        },
        show:{
            type: Boolean,
            default: true
        }
    }
}
</script>