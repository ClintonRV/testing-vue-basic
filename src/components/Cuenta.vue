<template>
    <h2>Tipo de Cuenta: {{cuenta}}</h2>
    <h2>Saldo: {{saldo}}</h2>
    <h2>Estado: {{estado?"Activo":"Inactivo"}}</h2>
    <div v-for="(servicio,index) in servicios" :key="index">
        {{index+1}} - {{servicio}}
    </div>
    <AccionSaldo texto="Aumentar saldo" @accion="aumentar"></AccionSaldo>
    <AccionSaldo texto="Disminuir saldo" @accion="disminuir" :sinSaldo="sinSaldo"></AccionSaldo>
</template>

<script>
import AccionSaldo from './AccionSaldo.vue'

export default {
    name: "Cuenta",
    components: {
        AccionSaldo
    },
    data() {
        return {
            saldo: 1000,
            cuenta: "Visa",
            estado: true,
            servicios:['giro','abono','transferencia'],
            sinSaldo: false
        }
    },
    methods:{
        aumentar(){
            this.saldo = this.saldo+100
            this.sinSaldo=false
        },
        disminuir(){
            if (this.saldo-100<0) {
                this.sinSaldo=true
                alert('No hay saldo suficiente')
            }
            else{
                this.sinSaldo=false
                this.saldo = this.saldo-100
            }
        }
    }
}
</script>

<style>

</style>