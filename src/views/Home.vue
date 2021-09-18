<template>
  <v-app :style="{ background: $vuetify.theme.themes.light.background }">
    <v-row>
      <v-col cols="8">
        <v-row
          :style="{ background: $vuetify.theme.themes.dark.background }"
          class="rounded-tr-x1 rounded-br-x1 fill-height"
        >
          <v-container>
            <v-row>
              <v-col cols="12" sm="12">
                <v-app-bar color="rgba(0,0,0,0)" flat class="mx-8 mb-8 mt-3">
                  <v-text-field
                    prepend-icon="mdi-magnify"
                    color="teal"
                    placeholder="Search your symptoms"
                    flat
                    success
                  >
                  </v-text-field>
                  <v-spacer></v-spacer>
                  <v-chip class="ma-2" color="white">
                    <v-icon left color="teal">mdi-clock-time-nine</v-icon>
                    14:02 AM Today Nov, 21
                  </v-chip>
                </v-app-bar>
              </v-col>

              <v-col cols="12" sm="12">
                <v-card
                  class="mx-12 rounded-tl-xl rounded-tr-xl rounded-bl-xl rounded-br-xl mt-n15"
                >
                  <v-list-item three-line>
                    <v-list-item-content class="pa-10">
                      <v-list-item-title class="headline mb-1">
                        today <span class="teal--text">-10%</span> discount
                        <br />
                        on lung examinations
                      </v-list-item-title>
                      <v-list-item-subtitle>
                        The package price includes: consultation<br />
                        of a pulmonogist, spirography, cardiogram
                        <span class="teal--text">></span>
                      </v-list-item-subtitle>
                    </v-list-item-content>
                    <v-list-item-avatar tile size="150" class="pr-10">
                      <img src="lungs.png" />
                    </v-list-item-avatar>
                  </v-list-item>
                </v-card>
              </v-col>
              <v-col cols="12" sm="12">
                <v-card
                  class="mx-12 rounded-tl-xl rounded-tr-xl rounded-bl-xl rounded-br-xl mt-n10"
                >
                  <v-app-bar color="rgba(0, 0, 0, 0)" flat class="ma-8">
                    <h5>Statistics of your health</h5>
                    <v-spacer></v-spacer>
                    <v-btn color="teal" text>
                      2019
                      <v-icon right>mdi-chevron-down</v-icon>
                    </v-btn>
                    <v-btn color="teal" rounded dark depressed>Year</v-btn>
                    <v-btn text>Month</v-btn>
                  </v-app-bar>
                  <template>
                    <v-sparkline
                      :value="value"
                      color="teal"
                      :smooth="radius || false"
                      :padding="padding"
                      :line-width="width"
                      :stroke-linecap="lineCap"
                      :fill="fill"
                      :type="type"
                      :auto-line-width="autoLineWidth"
                      auto-draw
                    >
                    </v-sparkline>
                  </template>
                </v-card>
              </v-col>
              <v-col cols="12" sm="6">
                <v-card
                  class="mx-12 rounded-tl-xl rounded-tr-xl rounded-bl-xl rounded-br-xl mt-n4"
                  color="teal"
                  dark
                >
                  <v-list-item three-line>
                    <v-list-item-content class="pa-2">
                      <v-list-item-title class="headline mb-1">
                        Heart rate <br />
                        <h2>112 bpm</h2>
                      </v-list-item-title>
                    </v-list-item-content>
                    <v-list-item-avatar tile size="100" class="pr-10">
                      <v-icon size="60">fas fa-heartbeat</v-icon>
                    </v-list-item-avatar>
                  </v-list-item>
                </v-card>
              </v-col>
              <v-col cols="12" sm="6">
                <v-card
                  class="mx-12 rounded-tl-xl rounded-tr-xl rounded-bl-xl rounded-br-xl mt-n12"
                >
                  <v-app-bar color="rgba(0, 0, 0, 0)" flat class="ma-8">
                    <h5>Your activity</h5>
                    <v-spacer></v-spacer>
                    <v-btn color="teal" rounded dark depressed>Week</v-btn>
                    <v-btn text>Month</v-btn>
                  </v-app-bar>
                  <v-progress-circular
                    v-for="progress in activityProgress"
                    :key="progress.color"
                    rotate="360"
                    size="70"
                    width="10"
                    :value="progress.value"
                    :color="progress.color"
                    class="mt-n5 ml-5 mb-2"
                    >{{ progress.value }}
                  </v-progress-circular>
                </v-card>
              </v-col>
            </v-row>
          </v-container>
        </v-row>
      </v-col>
      <v-col cols="4">
        <v-row
          :style="{ background: $vuetify.theme.themes.light.background }"
          class="fill-height"
        >
          <v-container>
            <v-row>
              <v-col cols="12" sm="12">
                <v-list two-line>
                  <v-list-item>
                    <v-list-item-avatar>
                      <img src="https://cdn.vuetifyjs.com/images/lists/3.jpg" />
                    </v-list-item-avatar>
                    <v-list-item-content>
                      <v-list-item-title>Anastasia Turner</v-list-item-title>
                      <v-list-item-subtitle class="teal--text"
                        >35 years, Houston</v-list-item-subtitle
                      >
                    </v-list-item-content>
                    <v-space></v-space>
                    <v-icon color="teal">mdi-menu</v-icon>
                  </v-list-item>
                </v-list>
              </v-col>
              <v-col
                cols="12"
                md="4"
                v-for="item in personalData"
                :key="item.value"
              >
                <v-row>
                  <v-col cols="12" md="2">
                    <v-card
                      height="50px"
                      width="100px"
                      :color="item.color"
                    ></v-card>
                  </v-col>
                  <v-col cols="12" md="10">
                    <v-list two-line subheader class="ml-n8">
                      <v-list-item>
                        <v-list-item-content>
                          <v-list-item-subtitle>{{
                            item.metric
                          }}</v-list-item-subtitle>
                          <v-list-item-title>{{
                            item.value
                          }}</v-list-item-title>
                        </v-list-item-content>
                      </v-list-item>
                    </v-list>
                  </v-col>
                </v-row>
              </v-col>
              <v-col cols="12" sm="12">
                <v-btn text
                  >November
                  <v-icon right>mdi-chevron-down</v-icon>
                </v-btn>
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
                <v-card
                  class="mx-12 rounded-tl-xl rounded-tr-xl rounded-bl-xl rounded-br-xl mt-n4 py-4"
                  :color="apointment.color"
                  :dark="apointment.dark"
                  flat
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
                </v-card>
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
                <v-card
                  class="mx-12 rounded-tl-xl rounded-tr-xl rounded-bl-xl rounded-br-xl mt-n4"
                  color="teal lighten-5"
                  flat
                >
                  <v-list-item three-line>
                    <v-list-item-avatar tile size="30">
                      <v-icon size="30">mdi-pill</v-icon>
                    </v-list-item-avatar>
                    <v-list-item-content class="pa-2">
                      <v-list-item-title class="headline mb-1">
                        Gentle Iron <br />
                        <h6>
                          <span class="teal--text">2 capsules</span> with meals
                          every day
                        </h6>
                      </v-list-item-title>
                    </v-list-item-content>
                  </v-list-item>
                </v-card>
              </v-col>
            </v-row>
          </v-container>
        </v-row>
      </v-col>
    </v-row>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      width: 2,
      radius: 10,
      padding: 8,
      lineCap: 'round',
      value: [0, 2, 5, 9, 5, 10, 3, 5, 0, 0, 1, 8, 2, 9, 0],
      fill: false,
      type: 'trend',
      autoLineWidth: false,
      activityProgress: [
        {
          value: 50,
          color: 'teal'
        },
        {
          value: 70,
          color: 'red'
        },
        {
          value: 80,
          color: 'blue'
        }
      ],
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
  },
  computed: {
    theme() {
      return this.$vuetify.theme.dark ? 'dark' : 'light'
    }
  }
}
</script>
