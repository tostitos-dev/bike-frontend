<template>
  <!-- <div class="google-map" :id="mapName"></div> -->
  <div>
    <static-map :google-api-key="apiKey"
			:language="language" v-on:get-url="getUrl" :paths="paths"
			:format="format" :markers="markers" :zoom="zoom" :center="center"
			:size="size" :type="type"></static-map>
  </div>
</template>

<style scoped>
  .google-map {
    margin: 0 auto;
    background: gray;
    width: 100%;
    height: 150px;
  }
</style>

<script>
  import StaticMap from 'vue-static-map';

  export default {
    name: 'google-map',
    components: {
      StaticMap
    },
    props: ['name','latitude', 'longitude'],
    data() {
      const dataValues = {
        apiKey: 'AIzaSyC8H8HLoD7qVny1-lxQKjLi5oH20MYpiPo',
        center: `${this.latitude}, ${this.longitude}`,
        format: 'JPEG',
        paths: [],
        getUrl: function(){},
        language: '',
        markers: [
          {
            label: 'B',
            color: 'ff5900',
            lat: this.latitude,
            lng: this.longitude,
            size: 'normal',
          }
        ],
        scale: '1',
        size: [300, 150],
        type: 'roadmap',
        url: '',
        zoom: 13,
      };
      return dataValues;
    },  
    // mounted: function () {
    //   const element = document.getElementById(this.mapName)
    //   const options = {
    //     zoom: 14,
    //     center: new google.maps.LatLng(this.latitude,this.longitude)
    //   }

    //   const map = new google.maps.Map(element, options);
    // }
  };
</script>
