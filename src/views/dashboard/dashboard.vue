<template>
  <div class="container">
    <episode-feed />

    <changelog />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

import CButton from '@/common/components/button.vue'
import EpisodeFeed from './components/episode-feed.vue'
import Changelog from './components/changelog.vue'

@Component({ components: { EpisodeFeed, Changelog, CButton } })
export default class Dashboard extends Vue {}
</script>

<style scoped lang="scss">
@import '../../colors';

.container {
  position: absolute;
  top: 80px;
  bottom: 0;
  width: 100%;

  display: grid;
  grid-template-columns: 28% 1fr;
  grid-template-rows: 100%;
  justify-items: center;
  align-items: center;
}

.route-enter-active,
.route-leave-active {
  transition: none 0.5s; // Required for Vue to realize there are transitions

  & > .episode-feed,
  & > .changelog {
    transition: opacity 0.5s, transform 0.5s;
  }
}

.route-enter,
.route-leave-to {
  & > .episode-feed {
    transform: translateX(-100%);
  }

  & > .changelog {
    opacity: 0;
    transform: translateY(-10%);
  }
}
</style>
