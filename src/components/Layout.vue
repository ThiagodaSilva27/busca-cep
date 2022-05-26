<template>
    <Navbar />
    <Lateral />
    <PesquisaCep />
</template>

<script>
import Navbar from "./Navbar.vue"
import Lateral from "./Lateral.vue"
import PesquisaCep from "./PesquisaCep.vue"
export default {
  name: 'Layout',
  components: {
      Navbar,
      Lateral,
      PesquisaCep
 }
}
</script>

<style src="../assets/css/styles.css" scoped/>
