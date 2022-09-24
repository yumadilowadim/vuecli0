<template>
  <div class="modal fade" id="carInfoModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLabel">{{ client_car[0] }}</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Закрыть"></button>
        </div>
        <div class="modal-body">
          <p><b>Привод:</b> {{ client_car[1] }}</p>
          <p><b>Двигатель:</b> {{ client_car[2] }}</p>
        </div>
        <!--div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Закрыть</button>
          <button type="button" class="btn btn-primary">Сохранить изменения</button>
        </div-->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CarsInfoModal',
  props: {
    client_car: Array
  }
}
</script>