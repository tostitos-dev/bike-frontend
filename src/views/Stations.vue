<template>
  <div class="stations">
    <Banner tabName='ESTACIONES'></Banner>
    <StationsList></StationsList>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import Banner from '@/components/Banner.vue'
import StationsList from '@/components/StationsList.vue'


export default {
  name: 'stations',
  components: {
    Banner,
    StationsList
  }
}
</script>

