<template>
  <table class="table table-striped table-sm">
    <thead>
    <tr>
      <th>#</th>
      <th>ФИО</th>
      <th>Автомобиль</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="client in clients" v-bind:key="client.id">
      <td>{{ client.id }}</td>
      <td>{{ client.client_name }}</td>
      <td><a href="#" @click="setModalInfo(client.client_car)" class="btn btn-primary btn-sm" data-bs-toggle="modal" data-bs-target="#carInfoModal" v-text="getCarName(client.client_car)"></a></td>
    </tr>
    </tbody>
  </table>
  <CarInfoModal :client_car="client_car" />
</template>

<script>
import CarInfoModal from '@/components/CarInfoModal.vue'

export default {
  name: 'ClientsList',
  components: {
    CarInfoModal
  },
  data() {
    return {
      client_car: []
    };
  },
  props: {
    clients: Object,
    cars: Object
  },
  methods: {
    setModalInfo(v_car_id) {
        let car_client_get = this.cars.find(el => el.id == v_car_id);
        let car_drive_actual = 'Полный'; let car_engine_actual = 'Бензин';
        if (car_client_get['car_drive'] == 1) { car_drive_actual = 'Полный'; } else { car_drive_actual = 'Передний'; }

        if (car_client_get['car_engine'] == 1) { car_engine_actual = 'Бензин';}
        if (car_client_get['car_engine'] == 2) { car_engine_actual = 'Дизель';}
        if (car_client_get['car_engine'] == 3) { car_engine_actual = 'Гибрид';}

        this.client_car[0] = car_client_get['car_brand']+' '+car_client_get['car_model'];
        this.client_car[1] = car_drive_actual;
        this.client_car[2] = car_engine_actual;
    }
  },
  computed: {
    getCarName(){
      return (v_car_id)=>{
        let car_client_get = this.cars.find(el => el.id == v_car_id);
        return car_client_get['car_brand']+' '+car_client_get['car_model'];
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
