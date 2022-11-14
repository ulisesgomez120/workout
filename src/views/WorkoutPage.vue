<template>
    <ion-page>
        <ion-content :fullscreen="true">
            <ion-header :translucent="true">
                <ion-toolbar>
                    <ion-title> {{ workout.name.replaceAll("_", " ") }} </ion-title>
                </ion-toolbar>
            </ion-header>

            <div id="container">
                <ion-grid>
                    <ion-row>
                        <ion-col>
                            <p>Sets</p>
                            <p><span>0</span>/{{ workout.sets }}</p>
                        </ion-col>
                        <ion-col>
                            <p>Reps</p>
                            <p>{{ workout.reps }}</p>
                        </ion-col>
                    </ion-row>
                </ion-grid>
                <ion-grid>
                    <ion-row>
                        <ion-col>
                            <p>RPE</p>
                            <p>{{ workout.rpe }}</p>
                        </ion-col>
                        <ion-col>
                            <p>Rest</p>
                            <p>{{ workout.rest }}</p>
                        </ion-col>
                    </ion-row>
                </ion-grid>
                <ion-grid>
                    <ion-row id="timer_row">
                        <ion-col>{{ timer_val }} </ion-col>
                        <ion-col v-if="total_seconds == 0">
                            <ion-button @click="timer_start()" fill="clear"><ion-icon size="large" :src="playCircleOutline"></ion-icon></ion-button>
                        </ion-col>
                        <ion-col v-else>
                            <ion-button @click="stop_timer()" fill="clear"><ion-icon size="large" :src="stopCircleOutline"></ion-icon></ion-button>
                        </ion-col>
                    </ion-row>
                </ion-grid>
                <ion-segment value="warm_up" @ionChange="segmentChanged($event)">
                    <ion-segment-button value="warm_up">
                        <ion-label>Warm-Up</ion-label>
                    </ion-segment-button>
                    <ion-segment-button value="working">
                        <ion-label>Working</ion-label>
                    </ion-segment-button>
                </ion-segment>
                <WorkoutForm></WorkoutForm>
                <PastWorkouts></PastWorkouts>
            </div>
        </ion-content>
    </ion-page>
</template>

<script lang="ts">
/* eslint-disable */
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonButton, IonLabel, IonItem, IonIcon, IonItemGroup, IonList, IonGrid, IonRow, IonCol, IonSegment, IonSegmentButton } from "@ionic/vue";
import { defineComponent } from "vue";
import { playCircleOutline, stopCircleOutline } from "ionicons/icons";
import { full_body_workouts } from "../workout_data";
import WorkoutForm from "../components/WorkoutForm.vue";
import PastWorkouts from "@/components/PastWorkouts.vue";

export default defineComponent({
    name: "WorkoutPage",
    components: {
        IonContent,
        IonHeader,
        IonPage,
        IonTitle,
        IonToolbar,
        IonButton,
        IonLabel,
        IonItem,
        IonIcon,
        IonItemGroup,
        IonList,
        IonGrid,
        IonRow,
        IonCol,
        IonSegment,
        IonSegmentButton,
        WorkoutForm,
        PastWorkouts,
    },
    data() {
        return {
            workout: {},
            playCircleOutline,
            stopCircleOutline,
            set_type: "warm_up",
            timer_ref: 0,
            timer_val: "00:00",
            total_seconds: 0,
        };
    },
    created() {
        const workouts = full_body_workouts.find((w) => w.id == this.$route.params.id);
        this.workout = workouts?.workouts[Number(this.$route.params.idx)] || {};
        console.log(this.workout);
    },
    methods: {
        segmentChanged(e: any) {
            this.set_type = e.detail.value;
        },
        timer_start() {
            const update_timer = () => {
                ++this.total_seconds;
                let min = (Math.floor(this.total_seconds / 60) + "").padStart(2, "0");
                let sec = ((this.total_seconds % 60) + "").padStart(2, "0");
                this.timer_val = min + ":" + sec;
            };
            this.timer_ref = setInterval(update_timer, 1000);
        },
        stop_timer() {
            clearInterval(this.timer_ref);
            this.timer_val = "00:00";
            this.total_seconds = 0;
        },
    },
});
</script>

<style scoped>
ion-grid {
    text-align: center;
}
.list {
    margin-top: 80px;
}
ion-col > p:first-of-type {
    background-color: rgb(255 255 255 / 10%);
    margin-left: auto;
    margin-right: auto;
    width: 80%;
}
#timer_row {
    border-top: 6px double #333;
}
#timer_row ion-col:first-of-type {
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>
