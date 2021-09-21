<template>
  <v-navigation-drawer app right v-model="drawer" width="500px">
    <v-container>
      <v-row>
        <v-col cols="12" sm="12">
          <v-toolbar flat>
            <v-avatar>
              <img src="https://cdn.vuetifyjs.com/images/lists/3.jpg" />
            </v-avatar>

            <v-toolbar-title class="ml-5">
              <h1 class="subtitle-1">Anastasia Turner</h1>
              <h1 class="subtitle-2 teal--text">35 years, Houston</h1>
            </v-toolbar-title>

            <v-spacer></v-spacer>

            <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
          </v-toolbar>
        </v-col>
        <v-col cols="12" md="4" v-for="item in personalData" :key="item.value">
          <v-alert :color="item.color" border="left" colored-border>
            <h1 class="subtitle-1 grey--text">{{ item.metric }}</h1>
            <h1 class="subtitle-1">{{ item.value }}</h1>
          </v-alert>
        </v-col>

        <v-col cols="4">
          <v-autocomplete
            auto-select-first
            chips
            small-chips
            deletable-chips
            :items="months"
            v-model="selectedMonth"
          ></v-autocomplete>
        </v-col>

        <v-col cols="12" sm="12">
          <v-list>
            <v-list-item>
              <v-list-item-content
                v-for="item in daysOfTheWeek"
                :key="item.day"
              >
                <v-btn
                  class="mr-1"
                  :outlined="!item.selected"
                  :dark="item.selected"
                  color="teal darken-1"
                  >{{ item.day }}</v-btn
                >
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-col>
        <v-col
          cols="12"
          sm="12"
          v-for="apointment in apointments"
          :key="apointment.staff"
        >
          <the-rounded-panel
            marginClass="mt-n4 py-4"
            :backgroundColour="apointment.color"
            :dark="apointment.dark"
            :flat="true"
          >
            <v-list-item three-line>
              <v-list-item-avatar tile size="30">
                <v-icon size="30">{{ apointment.icon }}</v-icon>
              </v-list-item-avatar>
              <v-list-item-content class="headline mb-1">
                {{ apointment.type }} <br />
                <h6>{{ apointment.timestamp }}</h6>
                <h6>{{ apointment.staff }}</h6>
              </v-list-item-content>
            </v-list-item>
          </the-rounded-panel>
        </v-col>
        <v-col cols="12" sm="12">
          <v-btn text
            >Your treatment
            <v-icon right>
              mdi-chevron-down
            </v-icon>
          </v-btn>
        </v-col>
        <v-col cols="12" sm="12">
          <the-rounded-panel
            marginClass="mt-n4"
            backgroundColour="teal lighten-5"
            :flat="true"
          >
            <v-list-item three-line>
              <v-list-item-avatar tile size="30">
                <v-icon size="30">mdi-pill</v-icon>
              </v-list-item-avatar>
              <v-list-item-content class="pa-2">
                <v-list-item-title class="headline mb-1">
                  Gentle Iron <br />
                  <h6>
                    <span class="teal--text">2 capsules</span> with meals every
                    day
                  </h6>
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </the-rounded-panel>
        </v-col>
      </v-row>
    </v-container>
  </v-navigation-drawer>
</template>

<script>
import TheRoundedPanel from './TheRoundedPanel.vue'

export default {
  components: {
    TheRoundedPanel
  },
  data() {
    return {
      drawer: true,
      months: [
        'January',
        'February',
        'March',
        'April',
        'May',
        'June',
        'July',
        'August',
        'September',
        'October',
        'November',
        'December'
      ],
      selectedMonth: 'November',
      personalData: [
        {
          metric: 'Blood',
          value: 'A+',
          color: 'green'
        },
        {
          metric: 'Height',
          value: '175 cm',
          color: 'red'
        },
        {
          metric: 'Weight',
          value: '64 kg',
          color: 'grey'
        }
      ],
      daysOfTheWeek: [
        {
          day: 'Mo',
          selected: false
        },
        {
          day: 'Tu',
          selected: false
        },
        {
          day: 'We',
          selected: false
        },
        {
          day: 'Th',
          selected: true
        },
        {
          day: 'Fr',
          selected: false
        },
        {
          day: 'Sa',
          selected: false
        }
      ],
      apointments: [
        {
          icon: 'mdi-tooth',
          type: 'Dentist',
          timestamp: '8:00 - 9:30',
          staff: 'Dr. Alex Brown (cab 39)',
          color: 'teal',
          dark: true
        },
        {
          icon: 'fas fa-heartbeat',
          type: 'Cardiologist',
          timestamp: '9:45 - 11:50',
          staff: 'Dr. Elika Clark (cab 61)',
          color: 'teal lighten-5',
          dark: false
        }
      ]
    }
  }
}
</script>

<style></style>
