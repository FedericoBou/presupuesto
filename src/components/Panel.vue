<template>
    <div class="sMenu">
        <br>
        <p class="text-center"><strong>Número de páginas</strong></p><b-button @click="valorPagina--" variant="success" size="sm">-</b-button>
        <input type="number" id="paginas"  v-model.number="valorPagina" class="mb-2" placeholder="Páginas">
        
        <b-button @click="valorPagina++"  size="sm" variant="success">+</b-button><b-button pill v-b-modal.my-modal variant="warning" size="sm">i</b-button>
        
        <hr>
        <p class="m-3 text-center"><strong>Número de idiomas</strong></p><b-button @click="valorIdioma--" variant="success"  size="sm">-</b-button>
         
        <input type="number" id="idiomas"  v-model.number="valorIdioma"  class="mb-4" placeholder="Idiomas">
         
        <b-button  @click="valorIdioma++"  size="sm" variant="success">+</b-button><b-button pill v-b-modal.my-modal2 variant="warning" size="sm">i</b-button>

        <b-modal id="my-modal">Lorem ipsum dolor sit amet.</b-modal>
        <b-modal id="my-modal2">Lorem ipsum dolor sit amet.</b-modal>


    </div>
</template>     

<script>
export default {
    name: 'Panel',
    props:{
        submenuVisible: Boolean,
    },
    data(){
        return{
            valorPagina: "",
            valorIdioma: "",
            visible: this.submenuVisible
        }
    },
    watch:{
        visible(val){
            this.submenuVisible = val;
        },
        valorPagina: function(){
            this.$emit('valorModificado', this.valorPagina );
        },
        valorIdioma: function(){
            this.$emit('valorModificadoIdioma', this.valorIdioma );
        },
    },
        created: function(){
            this.$emit('valorModificado', this.valorPagina, this.valorIdioma);
    }
    
    
}
</script>

<style scoped>

 input{
     margin: 5px;
    }
  button{
      margin: 3px;
  }  
  input{
      width: 100px;

  }
  .sMenu{
    text-align: center;
    border: 1px solid black;
    border-radius: 15px;
    
  }
</style>