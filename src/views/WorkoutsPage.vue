<template>
    <ion-page>
        <ion-content :fullscreen="true">
            <ion-header :translucent="true">
                <ion-toolbar>
                    <ion-title> Month </ion-title>
                </ion-toolbar>
            </ion-header>

            <div id="container">
                <ion-list class="list">
                    <ion-item-group>
                        <ion-item v-for="(wo, idx) in workouts" :key="wo.name">
                            <ion-label> {{ wo.name.replaceAll("_", " ") }}</ion-label
                            ><ion-button @click="workout_detail(idx)" fill="clear" size="large"><ion-icon :src="chevronForwardCircleOutline"></ion-icon></ion-button>
                        </ion-item>
                    </ion-item-group>
                </ion-list>
            </div>
        </ion-content>
    </ion-page>
</template>

<script lang="ts">
/* eslint-disable */
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonButton, IonLabel, IonItem, IonIcon, IonItemGroup, IonList } from "@ionic/vue";
import { defineComponent } from 'vue';
import { chevronForwardCircleOutline } from "ionicons/icons";
import { full_body_workouts } from "../workout_data";
import router from '@/router';

interface WO_Data {
    chevronForwardCircleOutline: string;
    workouts: object[];
}
export default defineComponent({
    name: "WorkoutsPage",
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
    },
    data() {
        const wo_data: WO_Data = {
            chevronForwardCircleOutline,
            workouts: [],
        };
        return wo_data;
    },
    mounted() {
        let wo = full_body_workouts.find((ele) => ele.id === this.$route.params.id);
        console.log(wo);
        this.workouts = wo?.workouts || [];
    },
    methods: {
        workout_detail(idx: number) {
            router.push('/workout/'+this.$route.params.id+'/'+idx);
        },
    }
});
</script>

<style scoped>
#container {
    text-align: center;
}
.list {
    margin-top: 80px;
}
</style>
