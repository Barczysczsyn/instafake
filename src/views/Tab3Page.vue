<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Perfil</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Perfil</ion-title>
        </ion-toolbar>
      </ion-header>
      <!--<p v-for="post in listPosts">{{post.author  }}</p>-->
      <ion-grid>
        <ion-row>
          <ion-col v-for="post in listPosts" size="4">
              <img :src="infoPerfil.avatar_url" :alt="infoPerfil.login">
          </ion-col>
          <ion-col>
            <p>{{ infoPerfil.public_repos }}</p>
            <p>publicacoes</p>
          </ion-col>
          <ion-col>
            <p>{{ infoPerfil.followers }}</p>
            <p>seguidores</p>
          </ion-col>
          <ion-col>
            <p>{{ infoPerfil.following }}</p>
            <p>seguindo</p>
          </ion-col>
        </ion-row>
      </ion-grid>
      <p>{{ infoPerfil.name }}</p>
      <p>@{{ infoPerfil.login }}</p>
      <p>{{ infoPerfil.bio }}</p>
      <ion-grid>
        <ion-row>
          <ion-col v-for="post in listPosts" size="4">
            <a :href="post.url">
              <img :src="post.download_url" :alt="post.author">
            </a>
          </ion-col>
        </ion-row>
      </ion-grid>

    </ion-content>
  </ion-page>
</template>

<script  lang="ts">
import { IonGrid, IonRow, IonCol, IonPage, IonHeader, IonToolbar, IonTitle, IonContent } from '@ionic/vue';
import MyPost from '@/classes/MyPosts'
export default{
  name: "Perfil",
  data(){
    return{
      infoPerfil: {},
      listPosts: [] as MyPost[]
    }
  },
  methods: {
    async getFotos(){
const fotos = await fetch("https://picsum.photos/v2/list?page=25");
this.listPosts = await fotos.json();
    },
    async getInfo(){
const infos = await fetch("https://api.github.com/users/carloscacho");
this.listPosts = await infos.json();
    }
  },
  mounted(){
    this.getFotos();
    this.getInfo();
  }
}
</script>
