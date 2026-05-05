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
            type: String,
            default: "success", 
            validator: function(value: string){
                return ["success","warning","danger"].includes(value)
            }
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