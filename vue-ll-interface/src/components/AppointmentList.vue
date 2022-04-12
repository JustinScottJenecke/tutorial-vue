<template>
    <div class="col-12 col-mid-10 col-lg-7">
        <div class="list-group list-group-flush">
            <div 
                class="list-group-item d-flex align-items-start" 
                v-for="(apt) in appointments" 
                :key="apt.aptIndex"
            >
                <!-- Del Button -->
                <button v-on:click="$emit('remove', apt)" class="mr-2 btn btn-sm btn-danger">
                    X
                </button>
                <!-- Informatin Section -->
                <div class="w-100">
                    <!-- Name and Date -->
                    <div class="d-flex justify-content-between">
                        <span class="h4 text-primary">{{apt.petName}}</span>
                        <span class="float-right">{{formattedDate(apt.aptDate)}}</span>
                    </div>
                    <!-- Owner Info -->
                    <div class="owner-name">
                        <span class="font-weight-bold text-primary mr-1">Owner:</span>
                        <span>{{apt.petOwner}}</span>
                    </div>
                    <!-- Notes -->
                    <div>
                        {{apt.aptNotes}}
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import moment from "moment";

export default ({

    name: "AppointmentList", 
    
    props: ["appointments"],

    methods: {

        formattedDate(dateArg) {
            return moment(new Date(dateArg)).format("MM-DD-YY, h:mm a")
        }
    }

})
</script>
