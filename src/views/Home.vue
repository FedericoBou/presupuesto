<template>
  <div class="home">
    <div class="container">
      <div class="row">
        <div class="col md-6 col-xs-12">
            
            <label class="chex"><input type="checkbox" id="web" :value = 500 v-model="marcados" @click="mostrarOpciones(true)" :formaction="sumaTotal"> Una página web: 500€</label>
            
            <panel v-show="submenu" :submenuVisible="submenu" @submenuVisibleEvent="mostrarOpciones" @valorModificado="sumaPaginas = $event" @valorModificadoIdioma="sumaIdiomas = $event"></panel>
            <br>
            <label><input type="checkbox" id="consultoria" :value= 300 v-model="marcados"> Una consultoria SEO: 300€</label>
            <br>
            <label><input type="checkbox" id="ads" :value= 200 v-model="marcados"> Una campaña de Ads: 200€</label> 
            <hr>
            <label class="total"><strong> Total: {{ sumaDelTotal + suma }}€ </strong></label>
        </div>
        
        <div class="col md-6 col-xs-12">
          <br>
          <lista :total= "sumaDelTotal + suma"></lista>
        </div>
      </div>  
    </div>  
    <b-button variant= "btn btn-success" id="volver" @click="bienvenida"> Página de Bienvenida</b-button>
  </div>
  
</template>

<script>

import Panel from '@/components/Panel.vue'
import Lista from '../components/Lista.vue'


export default {
  components:{ Panel, Lista},
  name: 'Home',
  data(){
    return{
      submenu: false,
      marcados: [],
      suma:0,
      sumaPaginas:1,
      sumaIdiomas:1,
      presupuestoFinal:0,

    }
  },
  methods:{
    mostrarOpciones(visible){
      this.submenu= visible;
    },
    bienvenida(){
      this.$router.push('/')
    }

  },
  computed: {
    sumaTotal: function(){  
      this.suma = 0;
      for( var i = 0; i < this.marcados.length; i++){
        this.suma += this.marcados[i];
      }
    },
    sumaDelTotal: function(){
      this.presupuestoFinal = 0;
        if(this.sumaPaginas != 0 || this.sumaIdiomas != 0){
          return this.presupuestoFinal = (this.sumaPaginas * this.sumaIdiomas * 30); 
         
    }
      this.sumaIdiomas = "";

      
    },
     
  },
}
</script>

<style scoped>
.home .total{
  border: 1px solid black;
  padding: 5px;
}
.home .container {
  text-align: left;
}

#volver{
  margin-top: 170px;
}



</style>
