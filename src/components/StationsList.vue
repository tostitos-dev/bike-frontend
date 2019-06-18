<template>
  <div class='container-fluid my-4'>
    <ul v-for="station in stations" v-bind:key="station.id" class="list-group">
      <li class="list-group-item mx-5 my-3">
        <div id='description' class='row'>
          <div class='col-4 map-style'>
            <Map v-bind:latitude="station.latitude" v-bind:longitude="station.longitude"></Map>
          </div>
          <div class='col-4'>
            <div class='center-align'>
              <p>Dirección : {{station.name}}</p>
              <p>Geolocalización : {{station.latitude}},{{station.longitude}}</p>
              <p>Última actualización : hace {{station.last_update}}</p>
            </div>
          </div>
          <div class='col-4 mt-2 d-inline-flex'>
            <div class='summary-card col-4'>
              <div class='card card-in-route'>
                <div class='card-body'>
                  <p>EN RUTA</p>
                  <p>{{station.empty_slots}}</p>
                </div>
              </div>
            </div>
            <div class='summary-card col-4'>
              <div class='card card-free'>
                <div class='card-body'>
                  <p>INACTIVAS</p>
                  <p>{{station.free_bikes}}</p>
                </div>
              </div>
            </div>
            <div class='summary-card col-4'>
              <div class='card card-total'>
                <div class='card-body'>
                  <p>USO</p>
                  <p>{{stationUse(station.empty_slots, station.free_bikes )}}%</p>
                </div>
              </div>
            </div>
          </div>
          
        </div>
      </li>
    </ul>
  </div>
</template>

<style scoped>
  .map-style{
    width:100%;
    height:150px;
  }
  .summary-card{
    padding-left: 5px;
    padding-right: 5px;
  }
  .center-align{
    padding-top:0.3rem;
  }
  .card-total{
    background-color:#ff5900;
    color: white;
  }
  .card-in-route{
    border-color: #ff5900;
  }
  .card-free{
    border-color: #004990;
  }
</style>

<script>
  import axios from "axios";
  import Map from '@/components/Map.vue'

  export default {
    name: 'stationslist',
    components: {
      Map
    },
    data(){
      return{
        stations: []
      }
    },
    methods:{
      async allStations(){
        let stationsApi = await axios.get('http://localhost:5000/api/v1/stations.json')
        this.stations = await stationsApi.data
        console.log(stationsApi.data)
      },
      stationUse(use, free){
        let total = use + free
        return ((use*100)/total).toFixed(1);
      }
    },
    created(){
      this.allStations()
    }
  }
</script>

