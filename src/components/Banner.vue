<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-light" style='padding:1rem;background-color: #ff5900'>
      <a class="navbar-brand" href="/">
        <img src="@/assets/logo.png" width="200" height="70" class="d-inline-block align-top" alt="">
      </a>

      <div class="collapse navbar-collapse options-nav" id="navbarNavAltMarkup">
        <div class="navbar-nav navbar-center">
          <a v-bind:class="{ 'active-tab': tabName==='SUMARIO' }"
            class="nav-item item-nav no-link" href="/">SUMARIO<span class="sr-only">(current)</span></a>
          <a v-bind:class="{ 'active-tab': tabName==='ESTACIONES' }"
            class="nav-item item-nav no-link" href="/stations">ESTACIONES</a>
        </div>
      </div>
    </nav>
    <div class='banner-container'>
      <img src="@/assets/banner2.jpg" style='opacity:0.8' width="100%" height="250px">
      <div class="bottom-left">
        <h1><strong>{{tabName}}</strong></h1>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Banner',
  props: {
    tabName: String
  }
}
</script>


<style scoped>
  h1{
    font-size:4rem;
  }
  .active-tab{
    text-decoration: underline !important;
  }
  .no-link{
    text-decoration: none;
  }
  .banner-container{    
    position: relative;
    text-align: center;
    color: white;
  }
  /* Bottom left text */
  .bottom-left {
    position: absolute;
    bottom: 0rem;
    left: 2rem;
  }

  .item-nav{
    color:white;
    padding-right:2rem;
    font-size: 1.8rem;
  }
  .navbar-nav.navbar-center {
    position: absolute;
    left: 50%;
    transform: translatex(-50%);
  }
</style>
