<template>
  <ion-card v-if="info">
    <ion-card-header>
      <ion-card-subtitle>
        {{ info["post code"] }}
      </ion-card-subtitle>
      <ion-card-title>
        {{ info["places"][0]["place name"] }}
      </ion-card-title>
    </ion-card-header>
    <ion-card-content>
      <ion-list>
        
        <ion-item>
          <ion-label>
            <strong>State:</strong>
            {{ info["places"][0]["state"] }} {{ info["places"][0]["state abbreviation"] }}
          </ion-label>
        </ion-item>
        
        <ion-item>
          <ion-label>
            <strong>Latitude:</strong>
            {{ info["places"][0]["latitude"] }}
          </ion-label>
        </ion-item>
        
        <ion-item>
          <ion-label>
            <strong>Longtitude:</strong>
            {{ info["places"][0]["longitude"] }}
          </ion-label>
        </ion-item>

      </ion-list>
    </ion-card-content>
  </ion-card>
</template>

<script>
import {
  IonCard,
  IonCardHeader,
  IonCardSubtitle,
  IonCardTitle,
  IonCardContent,
  IonList,
  IonItem,
  IonLabel,
} from "@ionic/vue";
export default {
  name: "ZipInfo",
  props: ["info"],
  components: {
    IonCard,
    IonCardHeader,
    IonCardSubtitle,
    IonCardTitle,
    IonCardContent,
    IonList,
    IonItem,
    IonLabel,
  },
};
</script>

<style>
</style>