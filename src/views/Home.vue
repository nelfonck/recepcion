<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo3.jpg">
    <p>{{info}}</p>
    <h4>Verificar recepcion de documentos electronicos</h4>
    <consulta /><resultado/>
  </div>
</template>

<script>
// @ is an alias to /src
import Consulta from '@/components/Consulta.vue'

import axios from 'axios'

export default {
  name: 'Home',
  components: {
    Consulta
  },
  data(){
    return{
      info:null
    } 
  }
}
</script>

<style >
    img {
      height: 100px;
    }
</style>
