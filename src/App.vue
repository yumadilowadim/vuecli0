<template>
  <div class="container">
    <nav>
      <div class="nav nav-tabs" id="nav-tab" role="tablist">
        <button class="nav-link active" id="nav-home-tab" data-bs-toggle="tab" data-bs-target="#nav-home" type="button" role="tab" aria-controls="nav-home" aria-selected="true">Машины</button>
        <button class="nav-link" id="nav-profile-tab" data-bs-toggle="tab" data-bs-target="#nav-profile" type="button" role="tab" aria-controls="nav-profile" aria-selected="false">Клиенты</button>
      </div>
    </nav>
    <LoaderCmp v-if="load" />
    <div v-if="!load" class="tab-content" id="nav-tabContent">
      <div class="tab-pane fade show active" id="nav-home" role="tabpanel" aria-labelledby="nav-home-tab" tabindex="0"><CarsList :cars="cars"/></div>
      <div class="tab-pane fade" id="nav-profile" role="tabpanel" aria-labelledby="nav-profile-tab" tabindex="0"><ClientsList :cars="cars" :clients="clients" /></div>
    </div>
  </div>
</template>

<script>
import CarsList from './components/CarsList.vue'
import ClientsList from './components/ClientsList.vue'
import LoaderCmp from './components/LoaderCmp.vue'
import "bootstrap/dist/css/bootstrap.min.css"
import "bootstrap/dist/js/bootstrap.min.js"
import "bootstrap"
import axios from "axios";

export default {
  name: 'App',
  components: {
    CarsList,ClientsList,LoaderCmp
  },
  data() {
    return {
      token: 'RbN_098uIu_po00NXZz',
      clients: null,
      cars: null,
      load: true
    };
  },
  mounted() {
    axios
        .get('http://yii2testapi/web/api/clients?access-token='+this.token)
        .then(response => (this.clients = response.data));
    axios
        .get('http://yii2testapi/web/api/cars/list?access-token='+this.token)
        .then(response => (this.cars = response.data, this.load = false));
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
