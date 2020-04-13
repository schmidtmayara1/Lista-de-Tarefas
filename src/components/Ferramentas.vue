<template>
<div id="ferramentas">
    <select v-model="caixaSel"> <!--A caixa selecionada vai para variável caixaSel-->
        <option value="" selected disabled>Selecione uma caixa</option>
        <option v-for="(caixa, index) in caixinhas" :key="index" :value="index">
        {{caixa.titulo}}
        </option>
        
        </select>
    <div id="paleta">
       <div class="cor1" :style="cor" v-for="(cor, index) in cores" :key="index" @click="alteraCor(cor)"></div>
       <!--Quando a cor foi clicada chama o método e passa a cor que foi  clicada-->
       <div id="texto">
           <input type="text" placeholder="Digite o nome da caixa" v-model="titulo">
        <button @click="alteraTexto">OK</button>
           </div>
           
   </div>
   

   </div>
</template>

<script>

export default {
    name: "Ferramentas",
    props: ['caixinhas'],
    data: function () {
        return {
            cores: ['background: pink','background: green','background: black'],
            caixaSel: '' ,
            titulo: ''
        } 
    }, methods: {
        alteraCor: function(cor) {
            this.$emit('alteraCor', {
                cor: cor,
                caixa: this.caixaSel
            }) 
        }, alteraTexto: function(){
            this.$emit('alterouTexto', {
                titulo: this.titulo ,
                caixa: this.caixaSel
            })
            
        }
    }
    

}

</script>

<style>
#ferramentas{
    width: 450px;
    height: 150px;
    border: 3px solid #ffffff;
    margin: 5px auto 0 auto;
    padding: 10px;
}
#ferramentas select{
    width: 250px;
    margin-bottom: 70px;
}
#paleta{
    width: 450px;
    height: 140px;
    display: flex;
}
.cor1{
    height: 50px;
    width: 50px;
    border: 1px solid #ffffff;
    margin-right: 3px;
}
</style>