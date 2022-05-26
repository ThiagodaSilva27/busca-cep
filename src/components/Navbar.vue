<template>
  <div class="navbar">
      <div class="campoDireito">
        <div class="logo">
          <router-link to="/">
            <img alt="folder" src="../assets/image/logo.svg">
          </router-link>
        </div>
        <div class="campoLocal">
          <!-- <span class="inputLocal">Surreal São Paulo</span> -->
          <div class="inputLocal">
            <h3>Surreal São Paulo</h3>
            <span>VTFx</span>
          </div>
        </div>
      </div>
    <div class="campoEsquerdo">
      <div class="sinoImg">
        <img alt="sino" src="../assets/image/icone-bell.svg">
      </div>
      <div class="nomeUsuario">
        <span>Olá Joaquim</span>
      </div>
    
        <img alt="usuario" src="../assets/image/usuario.svg" class="avatar">
      
    </div>
  </div>
</template>

<script>

export default {
  name: 'Navbar',
  // components: {
    
  // }
}
</script>

<style src="../assets/css/styles.css" scoped/>
