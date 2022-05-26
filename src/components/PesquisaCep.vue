<template>
<div class="layoutPesquisaCep">
    <vue-basic-alert 
       :duration="300" 
       :closeIn="3000" 
       ref="alert" />

  <div>
    <div>
      <input type="text" placeholder="insira o CEP" class="inputCep" v-model="cepAtual" v-on:keyup.enter="inserirCep()" />
     <button type="button" class="buttonAddEndereco" @click="inserirCep()">
       <div class="msgbutton">
        <img alt="folder" src="../assets/image/icone-plus.svg" class="iconePlus"> <span class="msgBtn">Adicionar endereço</span>
       </div>
      </button>
    </div>
  </div>
  <div class="cepsListados">
    <ul v-for="(cep, index) in ceps" :key="index">
      <li><img alt="folder" src="../assets/image/icone-lugar.svg"> <strong>CEP </strong>{{ cep }}</li>
    </ul>
  </div>
  <div class="botaoGerarEnderecos">
     <button type="button" class="buttonGerarEndereco" @click="gerarEnderecos()">
        Gerar endereços
    </button>
  </div>
  <hr class="cepsListados"/>
  <div v-for="(endereco, i) in cepsGerados" :key="i">
    <Card :rua="endereco.rua" :bairro="endereco.bairro" :cidade="endereco.cidade" :uf="endereco.uf" :cep="endereco.cep" @excluir-endereco="excluirEndereco" />
  </div>
</div>
</template>

<script>
import axios from 'axios'
import VueBasicAlert from 'vue-basic-alert'
import Card from "./Card.vue"
export default {
  name: 'PesquisaCep',
  components: {
    VueBasicAlert,
    Card
  },
  data () {
    return {
      ceps: [],
      cepAtual: "",
      cepsGerados: []
    }
  },
  methods: {
    async inserirCep() {
      const validarCep = await this.validadorCep();
      if (this.cepAtual !== "") {
        if (validarCep) {
          if (this.isExist()) {
            this.ceps.push(this.cepAtual.replace('-', ''))
          } else {
            this.$refs.alert.showAlert(
                'warning',
                'Este Cep já foi adicionado a lista',
                'Aviso'
            )
          }
        } else {
          this.$refs.alert.showAlert(
            'warning',
                'Por favor digite um cep valido',
                'CEP inválido'
            )
        }
      } else {
        this.$refs.alert.showAlert(
            'warning',
            'É necessário preencher o campo CEP',
            'Aviso'
        )
      }
      this.cepAtual = ""
    },
    async gerarEnderecos() {
      if (this.ceps.length > 0) {
        for (var i = 0; i < this.ceps.length;i++) {
          if (this.isExistGerador(this.ceps[i])) {
            await axios
             .get(`https://viacep.com.br/ws/${this.ceps[i]}/json/`)
             .then(response => 
               this.cepsGerados.push({
                 rua: response.data.logradouro,
                 bairro: response.data.bairro,
                 cidade: response.data.localidade,
                 uf: response.data.uf,
                 cep: response.data.cep
               })
             )
             .catch(error => console.log(error.message))
          }
        }
      } else {
        this.$refs.alert.showAlert(
            'warning',
            'É necessário possuir pelo menos 1 cep adicionado',
            'Aviso'
        )
      }
    },
    isExist() {
      const existe = this.ceps.some((cep) => cep === this.cepAtual);
      return !existe;
    },
    isExistGerador(cep) {
      const existe = this.cepsGerados.some((cepGerado) => cepGerado.cep.replace('-', '') === cep);
      return !existe;
    },
    async validadorCep() {
      let cepExistente = "";
      await axios
        .get(`https://viacep.com.br/ws/${this.cepAtual}/json/`)
        .then(response => 
          cepExistente = response.data.cep
        )
        .catch(error => console.log(error.message))
      if (cepExistente) {
        return true
      }
      return false
    },
    excluirEndereco(cep) {
      const cepAtual = cep.replace('-', '')
     const indice = this.cepsGerados.findIndex((ceps) => ceps.cep.replace('-', '') === cepAtual)
     this.cepsGerados.splice(indice, 1);
    },
  }
}
</script>

<style src="../assets/css/styles.css" scoped/>
