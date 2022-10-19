<template>
    <div class="form-inline d-flex justify-content-center" >
        
        <div class="form-group">
            <input type="text" class="form-control" placeholder="Consecutivo" v-model="consecutivo" @focus="total=''" ref="search" @keyup.enter="consumirapi(consecutivo,total)">
           
        </div>
        <div class="form-group ml-2">
            <input type="text" v-model="total" class="form-control ml-3" placeholder="Total" @focus="consecutivo=''" @keyup.enter="consumirapi(consecutivo,total)">
        </div>
        <div class="form-group ml-2">
            <button type="button" class="btn btn-primary" @click="consumirapi(consecutivo,total)">Buscar</button>
        </div>
       
            <resultados :info="info['data']"/> 
    </div>
   
</template>

<script>
import Resultados from './Resultados.vue'
import axios from 'axios'

export default {
    name:'Consulta',
    data(){
        return{
            info: [],
            iud:true,
            consecutivo: '',
            total:''
        }
    },
    components:{
        Resultados
    },
    methods:{
        consumirapi(consecutivo, total){
            this.$loading.show({delay:0})
                 axios
                .get('http://201.192.158.233:82/apibodega/public/recepcion/estado',{
                params:{
                    consecutivo: consecutivo,
                    total: total,
                    iud: true,
                    api_key : '$2y$10$ww4b.izY6lDO/.YgQGu4VeIeN5f8YlIgjNDXsZZmDsHBfJCdiyKXC',
                    
                }})
                .then((result) => {
                    console.log(result.data)
                    this.info = result;
                    this.$loading.hide() 
                    })  
                .catch(error => (this.info = error))
                this.consecutivo = '';
                this.total = '' ;
                this.setFocus() ;
                
        },
        setFocus:function(){
            this.$refs.search.focus();  
            }
        
    }
}
</script>

<style>

</style>