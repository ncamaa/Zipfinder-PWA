<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Blank</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content class="ion-padding" :fullscreen="true">
      <ZipSearch @get-zip="getZipInfo" />
      <ZipInfo v-bind:info="info" />
      <ClearInfo v-bind:info="info" @clear-info="clearInfo" />
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar, alertController } from '@ionic/vue';
import { defineComponent } from 'vue';
import ZipSearch from '../components/ZipSearch.vue';
import ZipInfo from '../components/ZipInfo.vue';
import ClearInfo from '../components/ClearInfo.vue';

export default defineComponent({
  name: 'Home',
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar,
    ZipSearch,
    ZipInfo,
    ClearInfo
  },
  data() {
    return {
      info: ''
    }
  },
  methods: {
    async getZipInfo(zip: any) {
      const res = await fetch(`https://api.zippopotam.us/us/${zip}`)
      if (res.status == 404) {
        this.showAlert();
      } else {
        this.info = await res.json()
        console.log(this.info)
      }
    },
    async showAlert() {
      const alert = await alertController
        .create({
          header: "Not a valid zipcode",
          message: "Please enter a valid US zipcode",
          buttons: ["OK"]
        })
      return alert.present()
    },
    clearInfo() {
      this.info = ''
    }
  },
});
</script>

<style scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  
  color: #8c8c8c;
  
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>