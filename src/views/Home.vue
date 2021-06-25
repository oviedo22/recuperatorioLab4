<template>
  <div class="home">
    <Grilla :entidades="this.entidades"></Grilla>
  </div>
</template>

<script>
import Grilla from '../components/Grilla.vue'

export default {
  name: 'Home',
  components: {
    Grilla
  },
  data(){
    return{
      entidades:[],      
    }

  },
  mounted(){
    this.getPaises()
  },
  methods:{
    
    async getPaises() {
       
      if(this.$route.query.callingcode){
        const res = await fetch("https://restcountries.eu/rest/v2/callingcode/"+this.$route.query.callingcode);        
        const resJson = await res.json();       
        this.entidades = resJson        
        if(!res.ok){           
          this.$router.push(`/`);    
        }
        
      }
      else if(this.$route.query.region){
        const res = await fetch("https://restcountries.eu/rest/v2/region/"+this.$route.query.region);
        const resJson = await res.json();        
        this.entidades = resJson        
      }

    }
  }
}
</script>
