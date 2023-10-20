<template>
    <ion-card>
      <ion-card-header>
        <div class="perfil">
      <img alt="Silhouette of mountains" src="https://ionicframework.com/docs/img/demos/card-media.png" />
      <ion-card-subtitle>Card Subtitle</ion-card-subtitle>
        </div>
      </ion-card-header>
  
      <img alt="Silhouette of mountains" src="https://ionicframework.com/docs/img/demos/card-media.png" />
      <ion-card-content>
        <div class="icons">
            <ion-icon icon="heart"></ion-icon>
            <p class="likes">numLikes</p>
            <ion-icon icon="chat"></ion-icon>
            <p class="comments">numComent</p>
            <ion-icon icon="send"></ion-icon>
            <ion-icon icon="bookmarker"></ion-icon>
        </div>
        <p class="legenda">usuario: legenda</p>
      </ion-card-content>
    </ion-card>
  </template>
  
  <script lang="ts">
    import { IonCard, IonCardContent, IonCardHeader, IonCardSubtitle, IonCardTitle, IonIcon } from '@ionic/vue';
    import { defineComponent } from 'vue';
  
    export default defineComponent({
      components: { IonCard, IonCardContent, IonCardHeader, IonCardSubtitle, IonCardTitle, IonIcon },
    });
  </script>

<style scoped>
.perfil{
display: flex;
    position: absolute;
}
.perfil img{
    width: 40px;
    height: 40px;
    border-radius: 50%;
    margin-right: 15px;
}
.icons{
    display: flex;
}
</style>