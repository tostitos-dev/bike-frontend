<template>
  <div class='mt-5'>
    <div class='row justify-content-center'>
      <div class='col-2'>
        <div class="card">
          <div class="card-body">
            <p> HOY </p>
            <p><strong> 16 </strong></p>
            <p> JUN 2019 </p>
          </div>
        </div>
      </div>

      <div class='col-6 vhr'>
        <div class='col-4'>
          <div class="card card-in-use">
            <div class="card-body text-center">
              <p> En ruta </p>
              <p> 999 </p>
            </div>
          </div>
        </div>
        <div class='col-4'>
          <div class="card card-free">
            <div class="card-body text-center">
              <p> Inactivas </p>
              <p> 999 </p>
            </div>
          </div>
        </div>
        <div class='col-4'>
          <div class="card card-total">
            <div class="card-body text-center">
              <p> Total </p>
              <p> 999 </p>
            </div>
          </div>
        </div>
      </div>
      
      <div class='col-2'></div>
    </div>
  </div>
</template>

<style scoped>
  p{
    font-size: 2rem;
  }
  .card-total{
    border-color:  #ff5900;
  }
  .card-in-use{
    border-color: #878787;
  }
  .card-free{
    border-color: #004990;

  }

  .vhr{
    border-right: 1px solid #333;
    border-left: 1px solid #333;

    height:250px;
  }
</style>
