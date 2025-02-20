<script>

  import HelloWorld from './components/HelloWorld.vue'

  import axios from 'axios'

  export default {
    name: 'App',

    data() {
      return {
        fields: ['nya', 'email', 'celular', 'genero', 'img'],
        _id: "",
        nya: "",
        email: "",
        celular: "",
        genero: "",
        img: "",
        listardatos: [],
      }
    },
    mounted() {
      axios.get('https://jsonplaceholder.typicode.com/users')
      .then(response => {

        this.listardatos = response.data;
        console.log(this.listardatos);

      })
      .catch(function (error){

        console.log(error)

      })
      .finally(function(){

        // Se ejecuto sin problemas

      });
    }


  }

</script>

<template>

  <div class="container">

    <table class="table" :items="listardatos" :fields="fields">
      <thead>
        <tr>
          <th scope="col">Nombre</th>
          <th scope="col">Email</th>
          <th scope="col">Celular</th>
          <th scope="col">Genero</th>
          <th scope="col">Imagen</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="ld in listardatos" v-bind:key="ld._id">
          <td>{{ ld.nya }}</td>
          <td>{{ ld.email }}</td>
          <td>{{ ld.celular }}</td>
          <td>{{ ld.genero }}</td>          
          <td>
            <img v-bind:src="'upload/' + ld.img" class="img-fluid ancho" width="30px" v-bind:alt="ld.nya">
          </td>          
        </tr>       
      </tbody>
    </table>

  </div>
 
</template>

<style scoped>

  .ancho {
    width: 30px;
  }

</style>
