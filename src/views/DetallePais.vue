<template>
  <div>
    <detalle-pais :pais="entidad"></detalle-pais>
  </div>
</template>

<script>
import DetallePais from "../components/DetallePais.vue";

export default {
  components:{
    'detalle-pais':DetallePais
  },
  data(){
    return{
      entidad: {}
    }
  },
  mounted(){
    this.getEntidad()    
  },
  methods:{
    async getEntidad() {
      const res = await fetch("https://restcountries.eu/rest/v2/name/"+this.$route.params.nombre);
        const resJson = await res.json();
        
        this.entidad = resJson[0]
        console.log(this.entidad)
    }
  }
}
</script>

<style>

</style>