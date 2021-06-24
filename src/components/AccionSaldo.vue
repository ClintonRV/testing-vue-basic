<template>
    <button @click="accion" :disabled="sinSaldo">{{texto}}</button>
</template>

<script>
export default {
    name: "AccionSaldo",
    props:{
        texto: String,
        sinSaldo: Boolean
    },
    methods:{
        accion(){
            this.$emit('accion')
        }
    }
}
</script>

<style>

</style>