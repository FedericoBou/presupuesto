<template>
    <div class="lista text-center">
        <h6>Nombre del presupuesto</h6>
        <input type="text" id="nombrePresupuesto" v-model="presupuesto">
        <h6>Cliente</h6>
        <input type="text" id="nombreCliente" v-model="cliente">
        <br><router-link :to="{query:{sum: total, clie: cliente, pres: presupuesto}}">
        <b-button v-on:click="cargoPresu" class="btn btn-success mt-3">Guardar Presupuesto</b-button>
        </router-link>
        <tabla :presu = "listado" ></tabla>

    </div>
</template>

<script>
import Tabla from '../components/Tabla.vue';

export default {
    components: {Tabla},
    name: "Lista",
    props: ['total'],
    data(){
        return{
            presupuesto:"",
            cargarPresupuesto:"",
            cliente:"",
            suma:"",
            listado: []
        }
    },
   methods:{
       cargoPresu: function(){
         const presu = {
             presupuesto: this.presupuesto,
             cliente: this.cliente,
             total: this.total
         };    
            this.listado.push(presu);
   },
  
    }
}
</script>