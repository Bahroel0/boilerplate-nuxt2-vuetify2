<template>
  <v-container class="pa-0" fluid style="height: 100vh; width: 100vw; background-color: #1a1917;">
    <!-- head title -->
    <v-row style="color: white" justify="center" align="center">
      <v-col lg="4">
        <v-row dense>
          <v-col cols="12">
            <span class="text-center">LAST UPDATE</span>
          </v-col>
          <v-col cols="12">
            SUNDAY, 27 JUNE 2020
          </v-col>
        </v-row>
      </v-col>
      <v-col lg="4">
        PRODUCT NAME
      </v-col>
      <v-col lg="4">
        <v-row class="text-end">
          <v-col cols="5">
            <v-row dense>
              <v-col cols="12">
                CURRENT DATE
              </v-col>
              <v-col cols="12">
                SUNDAY, 27 JUNE 2020
              </v-col>
            </v-row>
          </v-col>
          <v-col cols="5">
            <v-row dense>
              <v-col cols="12">
                CURRENT TIME
              </v-col>
              <v-col cols="12">
                00:00:00
              </v-col>
            </v-row>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
    <!-- end of head -->

    <!-- speedometer -->
    <v-row>
      <v-col v-for="i in 5" :key="i">
        <v-card outlined color="transparent" dark align="center">
          <v-card-text>
            <client-only>
              <VueSpeedometer
                :value="45"
                :max-value="100"
                :segments="3"
                :segment-colors="['#D32F2F', '#FFCA28', '#9CCC65']"
                text-color="white"
                current-value-text="45%"
                :height="200"
                :width="270"
              />
            </client-only>
            <span>OEE</span>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <!-- end of speedometer -->

    <!-- second row -->
    <v-row>
      <v-col v-for="i in 4" :key="i" cols="3">
        <v-card outlined color="transparent" dark>
          <v-card-title>
            Good Count
          </v-card-title>
          <v-card-text>
            <span class="h6">900</span>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <!-- end of second row  -->

    <!-- third row -->
    <v-row>
      <!-- first column -->
      <v-col cols="5">
        <v-row>
          <v-col cols="12">
            <v-card outlined color="transparent" dark>
              <v-card-title>
                Machine Status
              </v-card-title>
              <v-card-text>
                <span class="h6">900</span>
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="12">
            <v-card outlined color="transparent" dark>
              <v-card-title>
                Current Downtime
              </v-card-title>
              <v-card-text>
                <span class="h6">900</span>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-col>
      <!-- end of first column -->

      <!-- second column -->
      <v-col cols="7">
        <v-row>
          <v-col cols="6">
            <v-card outlined color="transparent" dark>
              <v-card-title>
                <v-row>
                  <v-col cols="12">
                    MOST COMMON DEFECT
                    <br>
                    325
                  </v-col>
                </v-row>
                <v-spacer />
                <v-icon>mdi-information</v-icon>
              </v-card-title>
              <v-divider />
              <v-card-text align="center">
                <client-only>
                  <VueApexchart type="pie" width="380" :options="chartOptions1" :series="series" />
                </client-only>
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="6">
            <v-card outlined color="transparent" dark>
              <v-card-title>
                <v-row>
                  <v-col cols="12">
                    DOWNTIME BY CAUSE
                    <br>
                    325
                  </v-col>
                </v-row>
                <v-spacer />
                <v-icon>mdi-information</v-icon>
              </v-card-title>
              <v-divider />
              <v-card-text align="center">
                <client-only>
                  <VueApexchart type="donut" width="380" :options="chartOptions2" :series="series" />
                </client-only>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-col>
      <!-- end of second column -->
    </v-row>
    <!-- end of third row -->
  </v-container>
</template>

<script>
import VueSpeedometer from 'vue-speedometer'
export default {
  components: { VueSpeedometer },
  layout: 'empty',
  data () {
    return {
      toggle: false,
      series: [44, 55, 13, 43, 22],
      chartOptions1: {
        chart: {
          width: 300,
          type: 'pie'
        },
        labels: ['Team A', 'Team B', 'Team C', 'Team D', 'Team E'],
        legend: {
          position: 'bottom'
        }
      },
      chartOptions2: {
        chart: {
          width: 100,
          type: 'donut'
        },
        labels: ['Team A', 'Team B', 'Team C', 'Team D', 'Team E'],
        legend: {
          position: 'bottom'
        }
      }
    }
  }
}
</script>
<style scoped>
.h6 {
  font-size: 2em;
}
</style>
