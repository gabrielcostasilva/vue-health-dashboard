<template>
  <v-app>
    <side-bar />

    <v-main>
      <router-view/>
    </v-main>

<user-bar></user-bar>
  </v-app>
</template>

<script>
import SideBar from './components/SideBar.vue'
import UserBar from './components/UserBar.vue'

export default {
  name: 'App',
  components: {
    SideBar,
    UserBar
  },
  data: () => ({
    //
  }),
};
</script>
