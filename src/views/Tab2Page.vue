<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Buscar</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Buscar</ion-title>
        </ion-toolbar>
      </ion-header>
      <div id="camera"></div>
      <div class="btns">
        <IonButton @click="tirarFoto()">
          Tirar Foto
        </IonButton>
      </div>
      <IonGrid>
        <IonRow>
          <IonCol size="4" v-for="foto in fotos">
            <IonImg :src="foto"></IonImg>
          </IonCol>
        </IonRow>
      </IonGrid>

      
      <ExploreContainer name="Buscar page" />
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonButton, IonGrid, IonRow, IonCol, IonImg} from '@ionic/vue';
import {CameraPreview} from "@capacitor-community/camera-preview";

export default{
name: "Criar",
data(){
  return{
    fotos:[] as string[]
  }
},
  components:{
    IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonButton, IonGrid, IonRow, IonCol, IonImg
  },
methods:{
  abrirCamera(){
    CameraPreview.start({
      parent:"camera",
      toBack: true,
      position: "front"

    })
  },
  async tirarFoto(){
    const foto = await CameraPreview.captureSample({quality: 50})
    const base64 = "data:image/jpeg;base64,"
    this.fotos = [base64 + foto.value, ...this.fotos]
  }
},
mounted(){
  this.abrirCamera();
}
}
</script>
