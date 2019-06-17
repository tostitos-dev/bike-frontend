<template>
  <div class="home">
    <Banner tabName="SUMARIO"></Banner>
    <Summary></Summary>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import Banner from '@/components/Banner.vue'
import Summary from '@/components/Summary.vue'

export default {
  name: 'home',
  components: {
    Banner,
    Summary
  }
}
</script>
