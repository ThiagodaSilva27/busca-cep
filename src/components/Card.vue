<template>
  <div class="card">
      <div class="alinhar">
        <div class="iconeLugar">
            <img alt="localização" src="../assets/image/icone-lugar.svg" class="imgLugarCard">
        </div>
        <div class="endereco">
            <h3>{{rua}}, {{bairro}}</h3>
            <span>{{cidade}} - {{uf}}</span>
        </div>
      </div>

      <div class="alinhar">
        <div class="cepCard">
            <span>{{cep}}</span>
        </div>
        <div class="lixo">
            <button 
                @click="$emit('excluirEndereco', cep)" 
                class="btnExcluir"
                >
                    <img alt="excluir" src="../assets/image/icone-lixo.svg" class="imgExcluir">
                </button>
        </div>
      </div>
  </div>
</template>

<script>
export default {
    name:"Card",
    emits: ['excluirEndereco'],
    props: {
        rua: String,
        cidade: String,
        bairro: String,
        uf: String,
        cep: String
    }
}
</script>

<style src="../assets/css/styles.css" scoped/>