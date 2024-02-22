<script>
import axios from 'axios'

export default {
  name: 'App',
  data() {
    return {
      fileds: ['nombre', 'primerapellido', 'segundoapellido', 'correo'],
      id: "",
      nombre: "",
      primerapellido: "",
      segundoapellido: "",
      correo: "",
      lista: [],
    }
  },
  mounted() {
    axios.get('https://apiexample.asociadosbega.com/public/contactos')
      .then(response => {
        this.lista = response.data;
        console.log(this.lista);
      })
      .catch(function (error) {
        console.log(error);
      })
      .finally(function () {

      })
  },
}
</script>

<template>
  <div class="container mt-3">
    <h2>API REST VUE</h2>
    <p>Consumiendo mi api de contactos</p>

    <div class="card" style="width:400px" v-for="lis in lista">
      <div class="card-body">
        <h4 class="card-title">{{ lis.nombre + ' ' + lis.primerapellido + ' ' + lis.segundoapellido}}</h4>
        <p class="card-text">{{ lis.correo }}</p>
        <a href="#" class="btn btn-primary">Contactar ahora</a><br><br>
      </div>
      <img class="card-img-bottom" src="https://cdn-icons-png.flaticon.com/512/3135/3135768.png" alt="Card image" style="width:100%">
    </div>

  </div>
</template>
