<template>
  <nav>
    <v-navigation-drawer
      v-model="drawer"
      dark
      app
      mini-variant
      mini-variant-width="100"
      class="teal"
    >
      <v-list>
        <v-list-item class="mb-12">
          <v-list-item-content>
            <v-icon class="mb-2" large>fas fa-hand-holding-medical</v-icon>
            <v-list-item-subtitle align="center">Medi</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <v-list flat>
        <v-list-item
          v-for="menuItem in menuItems"
          :key="menuItem.icon"
          router
          :to="menuItem.to"
        >
          <v-badge v-if="menuItem.highlight" color="pink" dot overlap>
            <v-list-item-content>
              <v-icon class="mb-2">{{ menuItem.icon }}</v-icon>
            </v-list-item-content>
          </v-badge>
          <v-list-item-content v-else>
            <v-icon class="mb-2">{{ menuItem.icon }}</v-icon>
          </v-list-item-content>
        </v-list-item>
      </v-list>
      <v-list style="position: absolute; bottom: 0" class="ml-3" flat>
        <v-list-item router to="/">
          <v-list-item-action>
            <v-icon right>fas fa-sign-out-alt</v-icon>
          </v-list-item-action>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      drawer: true,
      menuItems: [
        {
          highlight: false,
          to: '/',
          icon: 'fas fa-home'
        },
        {
          highlight: true,
          to: '/',
          icon: 'fas fa-user'
        },
        {
          highlight: false,
          to: '/',
          icon: 'fas fa-envelope'
        },
        {
          highlight: false,
          to: '/',
          icon: 'fas fa-cog'
        },
        {
          highlight: false,
          to: '/',
          icon: 'fas fa-question-circle'
        }
      ]
    }
  }
}
</script>
