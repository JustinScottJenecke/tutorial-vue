<!-- App Template -->
<template>
  <div id="main-app" class="container">

    <h4>{{ title }}</h4>

    <button class="mr-2">+ Add Appointment</button>

    <section>
      <br>
      <div v-for="(apt, i) in appointments" v-bind:key="i">
        <h4>Name: {{apt.petName}} </h4>
        <h5>Owner: {{apt.ownerName}} </h5>
        <p>
          {{ apt.aptNotes }}
          <br>
          Date: {{ apt.aptDate }}
        </p>
      </div>

    </section>
  </div>
</template>


<!-- App State -->
<script>
  import axios from "axios";

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
    components: {},

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
