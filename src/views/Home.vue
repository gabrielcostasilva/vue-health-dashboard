<template>
  <v-app :style="{ background: $vuetify.theme.themes.light.background }">
    <v-row>
      <v-col cols="12">
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
                <the-rounded-panel marginClass="mt-n15">
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
                </the-rounded-panel>
              </v-col>
              <v-col cols="12" sm="12">
                <the-rounded-panel marginClass="mt-n10">
                  <v-app-bar color="rgba(0, 0, 0, 0)" flat class="ma-8">
                    <h5>Statistics of your health</h5>
                    <v-spacer></v-spacer>
                    <v-col cols="6">
                      <v-autocomplete
                        multiple
                        auto-select-first
                        chips
                        deletable-chips
                        small-chips
                        :items="years"
                        v-model="selectedYears"
                      ></v-autocomplete>
                    </v-col>
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
                </the-rounded-panel>
              </v-col>
              <v-col cols="12" sm="6">
                <the-rounded-panel
                  backgroundColour="teal"
                  :dark="true"
                  marginClass="mt-n4"
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
                </the-rounded-panel>
              </v-col>
              <v-col cols="12" sm="6">
                <the-rounded-panel marginClass="mt-n12">
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
                </the-rounded-panel>
              </v-col>
            </v-row>
          </v-container>
        </v-row>
      </v-col>
    </v-row>
  </v-app>
</template>

<script>
import TheRoundedPanel from '../components/TheRoundedPanel.vue'

export default {
  components: {
    TheRoundedPanel
  },
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
      years: ['2019', '2020', '2021'],
      selectedYears: ['2019']
    }
  },
  computed: {
    theme() {
      return this.$vuetify.theme.dark ? 'dark' : 'light'
    }
  }
}
</script>
