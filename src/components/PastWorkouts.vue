<template>
    <div v-if="past_workouts.length > 0">
        <details v-for="wo in past_workouts" :key="wo.order">
            <summary>{{ wo.date }}</summary>
            <ion-list>
                <ion-item v-if="wo.type == 'warm-up'">Warm-Up: {{ wo.weight }} x {{ wo.reps }}</ion-item>
                <ion-item v-else>Working: {{ wo.weight }} x {{ wo.reps }}</ion-item>
            </ion-list>
        </details>
    </div>
    <div v-else></div>
</template>

<script lang="ts">
import { IonButton, IonItem, IonIcon, IonList } from "@ionic/vue";
import { defineComponent } from "vue";
import { chevronForwardCircleOutline } from "ionicons/icons";
import router from "@/router";

export default defineComponent({
    name: "HomePage",
    components: {
        // IonButton,
        IonItem,
        // IonIcon,
        IonList,
    },
    data() {
        return {
            chevronForwardCircleOutline,
            past_workouts: [{ date: "11/6/22 Sunday", weight: 120, reps: 4, type: "warm-up", alt_name: "", notes: "", order: 1 }],
        };
        //         past_wo_data= {
        // date: ‘11/1/22 Tuesday”
        // weight: 120
        // reps: 4
        // type: warm-up/working
        // alt_name: sub wo
        // notes: ‘sfkjals’
        // order: 1 [].length
    },
    methods: {
        nav_to_day(key: string) {
            router.push("/workouts/" + key);
        },
    },
});
</script>

<style scoped>
details {
    margin: 0 1.3rem 24px;
}
</style>
