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
export default {
  name: "main-app",
  // --- data ---
  data: function () {
    return {
      title: "Current Appointments:",

      appointments: [
        {
          petName: "Pepe",
          ownerName: "Reggie Tupp",
          aptNotes: "It's time for this rabbit's post spaying surgery checkup",
          aptDate: "2018-11-28 13:30",
        },
        {
          petName: "Rio",
          ownerName: "Philip Ransu",
          aptNotes: "Rio is up for his next round of vaccinations",
          aptDate: "2018-11-28 10:15",
        },
        {
          petName: "Scooter",
          ownerName: "Zachary Heilyn",
          aptNotes:
            "Scooter has been pawing at his ear and may have an ear infection",
          aptDate: "2018-11-28 14:45",
        },
        {
          petName: "Nadalee",
          ownerName: "Krystle Valerija",
          aptNotes:
            "This dog is coming in for his monthly nail trim and grooming",
          aptDate: "2018-11-28 16:00",
        },
        {
          petName: "Scout",
          ownerName: "Nicolette Bardeau",
          aptNotes:
            "This dog is coming in for his annual checkup and vaccinations",
          aptDate: "2018-11-28 9:00",
        },
      ],
    };
  },
  // --- components ---
  components: {},
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
