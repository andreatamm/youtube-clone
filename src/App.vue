<template>
  <v-app>
    <v-app-bar app color="black" dark>
      <v-toolbar-title class="text-h6">YouTube</v-toolbar-title>
      <v-spacer />
      <v-btn icon><v-icon>mdi-magnify</v-icon></v-btn>
      <v-btn icon><v-icon>mdi-account-circle</v-icon></v-btn>
    </v-app-bar>

    <v-navigation-drawer app color="black" dark>
      <v-list>
        <v-list-item v-for="item in menuItems" :key="item.title" link>
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <v-container fluid>
        <v-row>
          <v-col v-for="video in videos" :key="video.title" cols="12" sm="6" md="4" lg="3">
            <v-card class="bg-grey-darken-4" elevation="2">
              <v-img :src="video.thumbnail" height="180px" />
              <v-card-title class="text-white">{{ video.title }}</v-card-title>
              <v-card-subtitle class="text-grey-lighten-1">{{ video.channel }}</v-card-subtitle>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
import thumbnail from './assets/thumbnail.png' 

export default {
  data() {
    return {
      menuItems: [
        { title: 'Home', icon: 'mdi-home' },
        { title: 'Shorts', icon: 'mdi-video' },
        { title: 'Subscriptions', icon: 'mdi-bell' },
        { title: 'Library', icon: 'mdi-library-shelves' },
      ],
      videos: Array.from({ length: 12 }, (_, i) => ({
        title: `Video Title ${i + 1}`,
        channel: `Channel ${i + 1}`,
        thumbnail: thumbnail,
      })),
    }
  },
}
</script>

<style>
body {
  margin: 0;
  background-color: #121212;
}
</style>
