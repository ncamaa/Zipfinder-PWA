<template>
  <ion-grid>
    <form @submit.prevent="OnSubmit">
      <ion-col>
        <ion-item>
          <ion-label> Zipcode: </ion-label>
          <ion-input v-model="zip" name="zip" placeholder="Enter US Zipcode"></ion-input>
        </ion-item>
      </ion-col>
      <ion-col>
        <ion-button type="submit" color="primary" expand="block ">Find</ion-button>
      </ion-col>
    </form>
  </ion-grid>
</template>




<script>
import {IonGrid, IonItem, IonLabel, IonInput, IonCol, IonButton, alertController} from '@ionic/vue'
export default {
  name: "ZipSearch",
  components: {
    IonGrid, IonItem, IonLabel, IonInput, IonCol, IonButton
  },
  data() {
    return {
      zip: '',
    }
  },
  methods: {
    OnSubmit() {
      const isValidZip = /(^\d{5}$)|(^\d{5}-\d{4}$)/.test(this.zip);
      if(!isValidZip) {
        this.showAlert()
      } else {
        this.$emit('get-zip', this.zip)
      }
      this.zip = ''
    },
    async showAlert() {
      const alert = await alertController
        .create({
          header: "Not Valid",
          message: "Please enter a valid US zipcode",
          buttons: ["OK"]
        })
      return alert.present()
    }
  },
};
</script>

<style>
</style>