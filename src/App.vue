<template>
  <div>
      <h1>{{titulo}}</h1>
         <ul class="lista-fotos">
           <li v-for="foto in fotos" :key="foto._id" class="lista-fotos-item">    
            <img   :src="foto.url"  :alt="foto.titulo"  >
           </li>
         </ul>
  </div>
</template>

<script>
import axios from "axios";
export default {
  created() {
    axios
      .get("http://localhost:3000/v1/fotos")
      .then(resp => (this.fotos = resp.data));
  },

  data() {
    return {
      titulo: "Welcome to Vue",
      fotos: []
    };
  }
};
</script>


<!--
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style> -->
