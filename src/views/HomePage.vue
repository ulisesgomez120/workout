<template>
  <ion-page>
    <ion-content :fullscreen="true">
      <ion-header :translucent="true">
        <ion-toolbar>
          <ion-title>
            Full Body
          </ion-title>
        </ion-toolbar>
      </ion-header>
    
      <div id="container">
        <ion-list class="list">
          <ion-item-group>
            <ion-item-divider>
              <ion-label>
                Month 1
              </ion-label>
            </ion-item-divider>

            <ion-item v-for="n in 3" :key="n">
              <ion-label>Day {{n}}</ion-label><ion-button @click="nav_to_day('fbm1d'+n)" fill="clear" size="large"><ion-icon :src="chevronForwardCircleOutline"></ion-icon></ion-button>
            </ion-item>
          </ion-item-group>

          <ion-item-group>
            <ion-item-divider>
              <ion-label>
                Month 2
              </ion-label>
            </ion-item-divider>
            
            <ion-item v-for="n in 3" :key="n">
              <ion-label>Day {{n}}</ion-label><ion-button @click="nav_to_day('fbm2d'+n)" fill="clear" size="large"><ion-icon :src="chevronForwardCircleOutline"></ion-icon></ion-button>
            </ion-item>
          </ion-item-group>
        </ion-list>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, IonButton, IonLabel, IonItem, IonIcon, IonItemDivider, IonItemGroup, IonList } from '@ionic/vue';
import { defineComponent } from 'vue';
import { chevronForwardCircleOutline } from 'ionicons/icons';
import router from '@/router';

export default defineComponent({
  name: 'HomePage',
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
    IonItemDivider,
    IonItemGroup,
    IonList
  },
  data () {
    return {
      chevronForwardCircleOutline
    }
  },
  methods: {
    nav_to_day(key:string) {
      router.push('/workouts/'+key);
    }
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
