<script setup lang="ts">
import LeftPanel from './components/LeftPanel.vue';
import RightPanel from './components/RightPanel.vue';
</script>

<template>
  <div class="home">
    <LeftPanel />
    <RightPanel />
  </div>
</template>

<style lang="scss" scoped>
@import './assets/scss/variables.scss';

.home {
  background: grey;
}
</style>
