<template>
    <div class="tabla text-center"> 
        <br>
        <h3>Buscador</h3>
        <input type="text" v-model="search" placeholder="Buscador de presupuestos">
        <br>
        <hr>
        
        <table class="table">
            <tr>
                <th>Presupuesto</th>
                <th>Cliente</th>
                <th>total</th>
            </tr>
            
            <tr v-for = "(item, index) in buscador" :key = "index">
                <th> {{item.presupuesto}} </th>
                <th> {{item.cliente}} </th>
                <th> {{item.total}} </th>
            </tr>
            
        </table>
        
        <div class="botones  d-flex justify-content-center" role="group">
            <b-button type="button" class="btn btn-primary btn-sm m-2" @click = "newArray()" >Ordenar por letras</b-button>
            <b-button type="button" class="btn btn-primary btn-sm m-2" @click = "arrayTotal()" >Ordenar Precio</b-button>
            <b-button type="button" class="btn btn-primary btn-sm m-2" @click= "reinicio()" >Reiniciar</b-button>
        </div>
        <br>
        
  </div>
</template>

<script>

export default {
    props:["presu"],
    name:"Tabla",
        data(){
            return{
                alfa:[],
                ordenadoTotal:[],  
                reiniciar:[],
                search:"",
                item:[]
               
            }
        },

    methods :{ 

        newArray: function(){
            
            this.alfa = [...this.presu] ;
            
            function salida (a, b) {
                if (a.presupuesto > b.presupuesto){
                    return 1;
                }
                if(a.presupuesto < b.presupuesto){
                    return -1;
                }
                    return 0;
                
            };
            return this.presu.sort(salida); 
        }, 
    
        arrayTotal: function() {

            this.ordenadoTotal = [...this.presu];
                function salidaTotal(a, b) {
                  return a.total - b.total;    
                };
                return this.presu.sort(salidaTotal);
        },
        reinicio: function() {
            
            this.reiniciar = [...this.presu];
                return  this.reiniciar   
        },

    },

    computed: {
        buscador: function(){
            return this.presu.filter( item => 
                 item.presupuesto.includes(this.search));            
        }
    }

}

</script>