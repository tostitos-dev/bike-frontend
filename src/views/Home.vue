<template>
  <div class="home">
    <Banner tabName="SUMARIO"></Banner>
    <SummaryData></SummaryData>
    <hr class='mx-5'>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import Banner from '@/components/Banner.vue'
import SummaryData from '@/components/Summary.vue'

export default {
  name: 'home',
  components: {
    Banner,
    SummaryData
  }
}
</script>
