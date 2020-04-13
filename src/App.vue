<template>
  <div id="App">
    <caixas :caixinhas ="caixinhas"/> 
    <ferramentas :caixinhas ="caixinhas" @alteraCor="alteraCor($event)" @alterouTexto="alteraTexto($event)" /> 
    <!-- Quando o evento(click) ocorrer ele vau para 
    o met altecor e cor e pega a oq tem dentro da variável cor e leva para o event-->
  </div>
</template>

<script>

import Caixas from "./components/Caixas.vue"
import Ferramentas from "./components/Ferramentas.vue"

export default {
  name: "App",
  components: {
    Caixas,Ferramentas
  }, data: function() {
    return{
      caixinhas: [{
        titulo: "1",
        cor: "background: red"
      }, {
        titulo: "2",
        cor: "background: blue"
      }, {
        titulo: "3",
        cor: "background: orange"
      }]
    }
  }, methods: {
    alteraCor: function(event) {
      this.caixinhas[event.caixa].cor = event.cor
      
    }, alteraTexto: function(event){
      this.caixinhas[event.caixa].titulo = event.titulo

    }
  }
}

</script>

<style>

</style>
<!--console.log(`Caixa selecionada: ${event.caixa} Cor selecionada: ${event.cor}`) aparece em console-->