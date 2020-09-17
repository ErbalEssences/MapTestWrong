<template>
  <div>
    <div id="left">
    </div>
    <div id="right">
    </div>
    <img id="world" src="world.svg" alt="World">
    <div>
  </div>
  <div id="data">
      <svg  id="clock" width="231" height="170" viewBox="0 0 231 232" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path fill-rule="evenodd" clip-rule="evenodd" d="M115.502 0L0.000244141 115.6L115.502 231.199L231 115.601L115.502 0Z" fill="white"/>
        <rect x="125" y="105" width="16" height="64" transform="rotate(-180 125 105)" fill="#AE0000"/>
        <rect x="126.798" y="107.343" width="16" height="40" transform="rotate(-165 126.798 107.343)" fill="#AE0000"/>
      </svg>
      <div id="text">
        <p  id="city"><img id="flag" v-bind:src="locations[selectedLocation].flag" v-bind:alt="selectedLocation + ' flag'"> {{selectedLocation}}</p>
        <p  id="time">{{time}}</p>
      </div>
    </div>
    <div>
      <div v-for="city in locations" :key="city.name">{{city.name}}
        <input style="position: fixed;" type="radio" v-model="selectedLocation" v-bind:value="city.name" v-on:change="animateClock()">
      </div>
    </div>
  </div>
</template>

<script>



export default {
  name: 'World',
  data: () => ({
    selectedLocation: "New York",
    time: "",
    locations: {
      "New York":{
        name: "New York",
        flag: "us.svg",
        locales: "en-US",
        timeZone: "America/New_York",
      }, 
      "London": {
        name: "London",
        flag: "uk.svg",
        locales: "en-GB",
        timeZone: "England/London",
      }, 
      "San Francisco": {
        name: "San Francisco",
        flag: "us.svg",
        locales: "en-US",
        timeZone: "America/San_Francisco",
      }, 
      "Sydney": {
        name: "Sydney",
        flag: "au.svg",
        locales: "en-AU",
        timeZone: "Australia/Sydney",
      }, 
      "Last": {
        name: "Last",
        flag: "in.svg",
        locales: "en-IN",
        timeZone: "India",
      },  
    },
    rotationsHour: {
      1: "rotate(180 125 115)", 
      2: "rotate(180 125 115)", 
      3: "rotate(-90 125 115)", 
      4: "rotate(-120 125 115)", 
      5: "rotate(-160 125 115)", 
      6: "rotate(180 125 115)", 
      7: "rotate(180 125 115)", 
      8: "rotate(180 125 115)", 
      9: "rotate(90 125 115)", 
      10: "rotate(120 125 115)", 
      11: "rotate(160 125 115)", 
      12: "rotate(-180 125 115)", 
    },
    rotationsMinute: {
      0: "rotate(180 125 115)", 
      15: "rotate(180 125 115)",  
      30: "rotate(180 125 115)", 
      45: "rotate(180 125 115)", 
    },

  }),
  props: {},
  created() { this.animateClock(); },
  methods: {
    animateClock () {
      this.time = new Date().toLocaleTimeString(this.locations[this.selectedLocation].locales, this.locations[this.selectedLocation].timeZone);
      var hour = this.time.split(":")[1];
      var minute = this.time.split(":")[0];
      document.getElementsByTagName("rect")[1].setAttribute("transform", this.rotationsHour[hour])
      document.getElementsByTagName("rect")[0].setAttribute("transform", "rotate(180 125 115)")
      console.log(document.getElementsByTagName("rect")[1]);
      console.log(minute);
      
    }
  }
}





</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped lang="scss">
  $background-red: #ae0001;
  $dark-red: #640405;
  $land-red: #960202;

  #time {
    font-size:30px;
  }
  #city {
    font-size:20px;
  }
  #text {
    margin-left:180px;
    width: 100%;
  }
  #data {
    color: white;
    position: fixed;
    margin: 1.5%;
    max-width: 150px;
    z-index: 9999999999999;
    position: absolute;
    bottom: 3px;
    left: 3px;
  }
  #world {
    margin-top: 5%;
    margin-bottom: 15%;
    height: 75%;
    min-height: 75%;
    position: fixed;
    width: 100%;
  }
  #clock {
    margin: 1.5%;
    max-width: 150px;
    z-index: 9999999999999;
    position: absolute;
    bottom: 1%;
    left: 1%;
  }
  #left {
    background-color: $dark-red;
    opacity: 50%;
    min-height: 100%;
    position: fixed;
    width: 15%;
    height: 100%;
  }
  #right {
    background-color: $dark-red;
    opacity: 50%;
    min-height: 100%;
    position: fixed;
    width: 37%;
    height: 100%;
    right: 0;
  }
</style>