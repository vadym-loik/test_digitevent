<template>
    <div class="container">
        <div class="left__panel">
            <Math />
            <Date />
        </div>
        <div class="right__panel">
            <Logs />
        </div>
    </div>
</template>

<script lang="ts" setup>
import Math from '../components/Math.vue';
import Logs from '../components/Logs.vue';
import Date from '../components/Date.vue';
</script>

<style lang="scss" scoped>
@import '../assets/scss/variables.scss';

.container {
    display: grid;
    margin: 30px;
    padding: 30px;
}

.left__panel {
    display: flex;
    flex-direction: column;
}
</style>