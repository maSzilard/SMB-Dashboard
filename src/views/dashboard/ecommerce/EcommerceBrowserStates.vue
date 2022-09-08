<template>
  <b-card
    no-body
    class="card-browser-states"
  >
    <b-card-header>
      <div>
        <b-card-title>Social Images </b-card-title>
        <b-card-text class="font-small-2">
          October 2021
        </b-card-text>
      </div>

      <b-dropdown
        variant="link"
        no-caret
        class="chart-dropdown"
        toggle-class="p-0"
      >
        <template #button-content>
          <feather-icon
            icon="MoreVerticalIcon"
            size="18"
            class="text-body cursor-pointer"
          />
        </template>
        <b-dropdown-item href="#">
          Last 28 Days
        </b-dropdown-item>
        <b-dropdown-item href="#">
          Last Month
        </b-dropdown-item>
        <b-dropdown-item href="#">
          Last Year
        </b-dropdown-item>
      </b-dropdown>
    </b-card-header>

    <!-- body -->
    <b-card-body>
      <b-media>
        <img src="@/assets/images/pages/social-images/halloween.jpg" alt="" srcset="" width="550">
      </b-media>
    </b-card-body>
    <!--/ body -->
  </b-card>
</template>

<script>
import {
  BCard, BCardHeader, BCardTitle, BCardText, BCardBody, BMedia, BMediaAside, BMediaBody, BImg, BDropdown, BDropdownItem,
} from 'bootstrap-vue'
import VueApexCharts from 'vue-apexcharts'
import { $themeColors } from '@themeConfig'
/* eslint-disable global-require */
const $trackBgColor = '#e9ecef'
export default {
  components: {
    BCard,
    BCardHeader,
    BCardTitle,
    BCardText,
    BCardBody,
    BMedia,
    BMediaAside,
    BMediaBody,
    BImg,
    BDropdown,
    BDropdownItem,
    VueApexCharts,
  },
  data() {
    return {
      chartData: [],
      chartClone: {},
      chartColor: [$themeColors.primary, $themeColors.warning, $themeColors.secondary, $themeColors.info, $themeColors.danger],
      chartSeries: [54.4, 6.1, 14.6, 4.2, 8],
      browserData: [
        {
          browserImg: require('@/assets/images/icons/google-chrome.png'),
          name: 'Google Chrome',
          usage: '54.4%',
        },
        {
          browserImg: require('@/assets/images/icons/mozila-firefox.png'),
          name: 'Mozila Firefox',
          usage: '6.1%',
        },
        {
          browserImg: require('@/assets/images/icons/apple-safari.png'),
          name: 'Apple Safari',
          usage: '14.6%',
        },
        {
          browserImg: require('@/assets/images/icons/internet-explorer.png'),
          name: 'Internet Explorer',
          usage: '4.2%',
        },
        {
          browserImg: require('@/assets/images/icons/opera.png'),
          name: 'Opera Mini',
          usage: '8.%',
        },
      ],
      chart: {
        series: [65],
        options: {
          grid: {
            show: false,
            padding: {
              left: -15,
              right: -15,
              top: -12,
              bottom: -15,
            },
          },
          colors: [$themeColors.primary],
          plotOptions: {
            radialBar: {
              hollow: {
                size: '22%',
              },
              track: {
                background: $trackBgColor,
              },
              dataLabels: {
                showOn: 'always',
                name: {
                  show: false,
                },
                value: {
                  show: false,
                },
              },
            },
          },
          stroke: {
            lineCap: 'round',
          },
        },
      },
    }
  },
  created() {
    for (let i = 0; i < this.browserData.length; i += 1) {
      const chartClone = JSON.parse(JSON.stringify(this.chart))
      chartClone.options.colors[0] = this.chartColor[i]
      chartClone.series[0] = this.chartSeries[i]
      this.chartData.push(chartClone)
    }
  },
}
</script>
