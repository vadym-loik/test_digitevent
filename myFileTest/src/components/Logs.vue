<template>
    <div class="right__panel">
        <div class="log__card">
            <h3><span>Logs</span></h3>
            <ul>
                <p v-if="props" class="log__title">Math Fact</p>
                <li class="mathFact">{{ props }}</li>
            </ul>
            <ul>
                <p v-if="props" class="log__title">Date Fact</p>
                <li class="dateFact">{{ props }}</li>
            </ul>
        </div>

    </div>
</template>

<script setup lang="ts">
const props = defineProps({
    dateFactLog: Object,
    mathFactLog: Object,
});

console.log(props);

</script>

<style scoped>
@import '../assets/scss/variables.scss';

.right__panel {
    float: right;
    width: 70%;
}

.log__title {
    color: black;
    font-weight: 600;
}

.log__card {
    border: 1px solid #ccc;
    padding: 16px;
    margin-bottom: 16px;
    background: #fff;
    height: 100%;
}
</style>