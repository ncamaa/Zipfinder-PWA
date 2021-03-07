<template>
  <ion-button
    color="light"
    expand="block"
    v-if="info"
    @click="$emit('clear-info')"
    >Clear Info</ion-button
  >
</template>

<script>
import { IonButton } from "@ionic/vue";
export default {
  name: "ClearInfo",
  props: ["info"],
  components: {
    IonButton,
  },
};
</script>

<style>
</style>