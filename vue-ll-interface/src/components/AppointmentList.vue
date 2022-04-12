<template>
    <div class="col-12 col-mid-10 col-lg-7">
        <div class="list-group list-group-flush">
            <div 
                class="list-group-item d-flex align-items-start" 
                v-for="(apt, i) in appointments" 
                v-bind:key="i"
            >
                <button class="mr-2 btn btn-sm btn-danger">
                    X
                </button>
                <div class="w-100">
                    <div class="d-flex justify-content-between">
                        <span class="h4 text-primary">{{apt.petName}}</span>
                        <span class="float-right">{{formattedDate(apt.aptDate)}}</span>
                    </div>
                    <div class="owner-name">
                        <span class="font-weight-bold text-primary mr-1">Owner:</span>
                        <span>{{apt.petOwner}}</span>
                    </div>
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
