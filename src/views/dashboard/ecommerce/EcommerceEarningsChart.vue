<template>
  <b-card
    v-if="data"
    class="earnings-card"
  >
    <b-row>
      <b-col cols="6">
        <b-card-title class="mb-1">
          Earnings
        </b-card-title>
        <div class="font-small-2">
          This Half Year
        </div>
        <h5 class="mb-1">
          £924,831.83
        </h5>
        <b-card-text class="text-muted font-small-2">
          <span class="font-weight-bolder">9%</span><span> more earnings than last month.</span>
        </b-card-text>
      </b-col>
      <b-col cols="6">
        <!-- chart -->
        <vue-apex-charts
          height="120"
          :options="earningsChart.chartOptions"
          :series="data.series"
        />
      </b-col>
    </b-row>
  </b-card>
</template>

<script>
import {
  BCard, BRow, BCol, BCardTitle, BCardText,
} from 'bootstrap-vue'
import VueApexCharts from 'vue-apexcharts'
import { $themeColors } from '@themeConfig'

const $earningsStrokeColor2 = '#28c76f66'
const $earningsStrokeColor3 = '#28c76f33'
export default {
  components: {
    BCard,
    BRow,
    BCol,
    BCardTitle,
    BCardText,
    VueApexCharts,
  },
  props: {
    data: {
      type: Object,
      default: () => {},
    },
  },
  data() {
    return {
      earningsChart: {
        chartOptions: {
          chart: {
            type: 'donut',
            toolbar: {
              show: false,
            },
          },
          dataLabels: {
            enabled: false,
          },
          legend: { show: false },
          comparedResult: [12, 5, 1, 1],
          labels: ['WF', 'BR', 'HSO', 'GAC'],
          stroke: { width: 0 },
          colors: [$earningsStrokeColor2, $earningsStrokeColor3, $themeColors.success],
          grid: {
            padding: {
              right: -20,
              bottom: -8,
              left: -20,
            },
          },
          plotOptions: {
            pie: {
              startAngle: -10,
              donut: {
                labels: {
                  show: true,
                  name: {
                    offsetY: 15,
                  },
                  value: {
                    offsetY: -15,
                    formatter(val) {
                      // eslint-disable-next-line radix
                      return `${parseInt(val)}%`
                    },
                  },
                  total: {
                    show: true,
                    offsetY: 15,
                    label: 'WF',
                    formatter() {
                      return '72%'
                    },
                  },
                },
              },
            },
          },
          responsive: [
            {
              breakpoint: 1325,
              options: {
                chart: {
                  height: 100,
                },
              },
            },
            {
              breakpoint: 1200,
              options: {
                chart: {
                  height: 120,
                },
              },
            },
            {
              breakpoint: 1045,
              options: {
                chart: {
                  height: 100,
                },
              },
            },
            {
              breakpoint: 992,
              options: {
                chart: {
                  height: 120,
                },
              },
            },
          ],
        },
      },
    }
  },
}
</script>
