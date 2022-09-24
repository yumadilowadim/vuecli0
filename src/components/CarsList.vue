<template>
  <table class="table table-striped table-sm">
    <thead>
    <tr>
      <th>#</th>
      <th>Наименование</th>
      <th>Двигатель</th>
      <th>Привод</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="car in cars" v-bind:key="car.id">
      <td>{{ car.id }}</td>
      <td>{{ car.car_brand }} {{ car.car_model }}</td>
      <td>{{ getEngine(car.car_engine) }}</td>
      <td>{{ getDrive(car.car_drive) }}</td>
    </tr>
    </tbody>
  </table>

</template>

<script>
export default {
  name: 'CarsList',
  props: {
    cars: Object
  },
  computed: {
    getDrive(){
      return (v_drive)=>{
        if (v_drive == 1) {
          return 'Полный';
        } else { return 'Передний'; }
      }
    },
    getEngine(){
      return (v_engine)=>{
        if (v_engine == 1) { return 'Бензин';}
        if (v_engine == 2) { return 'Дизель';}
        if (v_engine == 3) { return 'Гибрид';}
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
