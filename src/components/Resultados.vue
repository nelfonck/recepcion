<template>


<div class="table-responsive" >

  <table class="table mt-2 w-100 " >
  <thead class="thead-dark">
    <tr>
      <th scope="col">Consecutivo</th>
      <th scope="col">Proveedor</th>
      <th scope="col">Fecha emision</th>
      <th scope="col">Cliente</th>
      <th scope="col">Total</th>
     <th scope="col">Msj hacienda</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="inf in info" :key="inf.id">
      <th scope="row">{{inf.consecutivo_documento}}</th>
      <td>{{inf.nombre_vendedor}}</td>
      <td>{{inf.fecha_emision_documento}}</td>
      <td>{{inf.cliente}}</td>
      <td>{{inf.total}}</td>
      <td>{{inf.mensaje_hacienda}}</td>
    </tr>
  
  </tbody>
</table>
</div>


    
</template>

<script>
export default {
    name:'Resultados',
    props:{
      info: {
        type: Array,
        required: true
      }
    }
}
</script>

<style>
  .container{
    width: 100%;
    }
</style>