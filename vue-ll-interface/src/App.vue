<!-- App Template -->
<template>
  <div id="main-app" class="container">

    <div class="row justify-content-center">
      <appointment-list v-bind:appointments="appointments" v-on:remove="removeApt"/>
    </div>
    
  </div>
</template>


<!-- App State -->
<script>
  import axios from "axios"
  import AppointmentList from "./components/AppointmentList.vue"
  import _ from "lodash"

  export default {

    // -- template --
    name: "main-app",
    
    // -- data --
    data: function () {
      return {
        appointments: [],
        aptIndex: 0
      };
    },

    // -- components --
    components: {
      AppointmentList
    },

    // -- lifecycle hooks --
    mounted() {
      axios.get("../data/appointments.json")
        .then( response => (this.appointments = response.data.map( apt => {

            apt.aptId = this.aptIndex
            this.aptIndex++

            return apt
          })
        ) 
      )
    },

    // methods
    methods: {
      // lodash function that filters out
      removeApt(apt) {
        this.appointments = _.without(this.appointments, apt)
      }
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
