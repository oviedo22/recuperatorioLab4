<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="dark">
      <b-navbar-brand href="/">NavBar</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-form v-on:submit.prevent="onSubmit(codigo)">
            <b-nav-text class="mx-2">Código Pais:</b-nav-text>
            <b-form-input
              class="mx-2"
              v-model="codigo"
              placeholder="Search"
            ></b-form-input>
            <b-button
              variant="success"
              class="my-2 my-sm-0"
              type="submit"
              v-bind:to="`/?callingcode=${codigo}`"
              >Search</b-button
            >
          </b-nav-form>
          <b-nav-text class="mx-2">Regiones:</b-nav-text>
          <b-nav-item-dropdown text="-SELECCIONE UNA REGIÓN-" right>
          <b-dropdown-item @click="getPaisesXRegion('africa')">Africa</b-dropdown-item>
          <b-dropdown-item @click="getPaisesXRegion('asia')">Asia</b-dropdown-item>
          <b-dropdown-item @click="getPaisesXRegion('americas')">Americas</b-dropdown-item>
          <b-dropdown-item @click="getPaisesXRegion('europe')">Europe</b-dropdown-item>
          <b-dropdown-item @click="getPaisesXRegion('oceania')">Oceania</b-dropdown-item>
        </b-nav-item-dropdown>
          
          
        </b-navbar-nav>

        <!-- Right aligned nav items -->
      </b-collapse>
    </b-navbar>
  </div>
</template>
<script>
export default {  
  data() {
    return {
      codigo: "",
      entidades:[]
    };
  },
  methods: {
    onSubmit(codigo) {     
      this.$router.push(`/?callingcode=${codigo}`);
    },
    getPaisesXRegion(region){
      this.$router.push(`/?region=${region}`);

    },    
    
  },
};
</script>

<style lang="">
</style>