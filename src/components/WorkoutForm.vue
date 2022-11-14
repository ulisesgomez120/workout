<template>
    <ion-item>
        <ion-label>Weight</ion-label>
        <ion-input id="set_weight" type="number"></ion-input>
    </ion-item>
    <ion-item>
        <ion-label>Reps</ion-label>
        <ion-input id="set_reps" type="number"></ion-input>
    </ion-item>
    <ion-item>
        <ion-label>Alt Name</ion-label>
        <ion-input id="set_alt"></ion-input>
    </ion-item>
    <ion-item>
        <ion-label position="stacked">Notes</ion-label>
        <textarea id="set_notes" rows="4"></textarea>
    </ion-item>
    <ion-button expand="full">Add</ion-button>

    <!-- <ion-button @click="timer_start()" fill="clear"><ion-icon size="large" :src="playCircleOutline"></ion-icon></ion-button> -->
</template>

<script lang="ts">
/* eslint-disable */
import { IonInput, IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonButton, IonLabel, IonItem, IonIcon, IonItemGroup, IonList, IonGrid, IonRow, IonCol } from "@ionic/vue";
import { defineComponent } from "vue";
// import { playCircleOutline, stopCircleOutline } from "ionicons/icons";
// import { full_body_workouts } from "../workout_data";

export default defineComponent({
    name: "WorkoutPage",
    components: {
        IonInput,
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
    },
    data() {
        return {
            workout: {},
        };
    },
    created() {},
    methods: {},
});
</script>

<style scoped>
ion-item {
    margin: 21px 0;
}
#set_notes {
    width: 100%;
}
ion-button {
    margin: 14px 0 24px;
}
textarea {
    margin: 8px 0;
}
</style>
