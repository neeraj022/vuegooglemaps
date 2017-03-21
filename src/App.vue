<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view></router-view>
    <label>
          Das Label
          <gmap-autocomplete :value="description"
            @place_changed="setPlace">
          </gmap-autocomplete>
    </label>
  </div>
</template>

<script>
import * as VueGoogleMaps from 'vue2-google-maps'
import Vue from 'vue'

Vue.use(VueGoogleMaps, {
  load: {
    key: 'AIzaSyBzlLYISGjL_ovJwAehh6ydhB56fCCpPQw',
    libraries: 'places'
  }
})

export default {
  name: 'app'
}

new Vue({
    el: '#app',
    data: {
      description: 'Singapore',
      latLng: {}
    },
    methods: {
      setDescription(description) {
        this.description = description;
      },
      setPlace(place) {
        this.latLng = {
          lat: place.geometry.location.lat(),
          lng: place.geometry.location.lng(),
        };
      }
    }
  });
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
