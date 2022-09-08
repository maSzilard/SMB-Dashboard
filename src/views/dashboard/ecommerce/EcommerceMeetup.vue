<template>
  <b-card v-if="data" no-body class="card-developer-meetup">
    <div class="bg-light-primary rounded-top text-center">
      <b-img
        :src="require('@/assets/images/illustration/email.svg')"
        alt="Meeting Pic"
        height="170"
      />
    </div>
    <b-card-body>
      <!-- metting header -->
      <div class="meetup-header d-flex align-items-center">
        <div class="meetup-day">
          <h6 class="mb-0">THU</h6>
          <h3 class="mb-0">06</h3>
        </div>
        <div class="my-auto">
          <b-card-title class="mb-25"> Coffe and cake meeting </b-card-title>
          <b-card-text class="mb-0"> 10 AM to 11 AM10 AM to 11 AM </b-card-text>
        </div>
      </div>
      <!--/ metting header -->

      <!-- metting header -->
      <div class="meetup-header d-flex align-items-center">
        <div class="meetup-day">
          <h6 class="mb-0">WED</h6>
          <h3 class="mb-0">07</h3>
        </div>
        <div class="my-auto">
          <b-card-title class="mb-25">
            Coffe and cake meeting + JMS
          </b-card-title>
          <b-card-text class="mb-0"> 12 AM to 1PM </b-card-text>
        </div>
      </div>
      <!--/ metting header -->

      <!-- metting header -->
      <div class="meetup-header d-flex align-items-center">
        <div class="meetup-day">
          <h6 class="mb-0">MON</h6>
          <h3 class="mb-0">12</h3>
        </div>
        <div class="my-auto">
          <b-card-title class="mb-25"> Teambuilding: boardgame </b-card-title>
          <b-card-text class="mb-0"> 6 PM to 8 PM </b-card-text>
        </div>
      </div>
      <!--/ metting header -->

    </b-card-body>
  </b-card>
</template>

<script>
import {
  BCard,
  BImg,
  BCardBody,
  BCardText,
  BCardTitle,
  BMedia,
  BMediaAside,
  BAvatar,
  BAvatarGroup,
  VBTooltip,
  BMediaBody,
} from "bootstrap-vue";

export default {
  components: {
    BCard,
    BImg,
    BCardBody,
    BCardText,
    BCardTitle,
    BMedia,
    BMediaAside,
    BAvatar,
    BAvatarGroup,
    BMediaBody,
  },
  directives: {
    "b-tooltip": VBTooltip,
  },
  props: {
    data: {
      type: Object,
      default: () => {},
    },
  },
};
</script>