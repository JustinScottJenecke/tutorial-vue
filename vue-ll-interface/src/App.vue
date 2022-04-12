<!-- App Template -->
<template>
  <div id="main-app" class="container">

    <div class="row justify-content-center">
      <appointment-list v-bind:appointments="appointments"/>
    </div>
    
  </div>
</template>


<!-- App State -->
<script>
  import axios from "axios";
  import AppointmentList from "./components/AppointmentList.vue";

  export default {

    // -- template --
    name: "main-app",
    
    // -- data --
    data: function () {
      return {
        title: "Current Appointments:",
        appointments: []
      };
    },

    // -- components --
    components: {
      AppointmentList
    },

    // -- lifecycle hooks --
    mounted() {
      axios.get("../data/appointments.json")
        .then( response => (this.appointments = response.data) )
    }
  };
</script>


<!-- App Style -->
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
