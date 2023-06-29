<template>
    <div class="app">
        <div class="container">
            <div class="left-panel">
                <div class="card">
                    <h2>A cool Maths fact</h2>
                    <i class="ri-arrow-down-circle-line" @click="fetchMathFact"></i>
                    <p>{{ mathFact }}</p>

                </div>
                <div class="card">
                    <h2>A cool Date fact</h2>
                    <i class="ri-arrow-down-circle-line" @click="fetchDateFact"></i>
                    <p>{{ dateFact }}</p>

                </div>
            </div>
            <div class="right-panel">
                <div class="log__card">
                    <h2>Logs</h2>
                    <ul>
                        <p>Math Fact</p>
                        <li class="mathFact" v-for="fact in mathFactLog" :key="fact">{{ fact }}</li>
                    </ul>
                    <ul>
                        <p>Date Fact</p>
                        <li class="dateFact" v-for="fact in dateFactLog" :key="fact">{{ fact }}</li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import axios from 'axios';

const mathFact = ref('');
const dateFact = ref('');


const mathFactLog = ref<string[]>([]);
const dateFactLog = ref<string[]>([]);

const fetchMathFact = async () => {
    try {
        const response = await axios.get('http://numbersapi.com/random/math');
        mathFact.value = response.data;
        mathFactLog.value.push(mathFact.value);
    } catch (error) {
        console.error(error);
    }
};

const fetchDateFact = async () => {
    try {
        const response = await axios.get('http://numbersapi.com/random/date');
        dateFact.value = response.data;
        dateFactLog.value.push(dateFact.value);
    } catch (error) {
        console.error(error);
    }
};
</script>

<style lang="scss" scoped>
@import '../assets/scss/variables.scss';


.app {
    background: grey;
}

.container {
    display: flex;
    justify-content: space-between;
    margin: 30px;
    padding: 30px;
}

.left-panel {
    width: 50%;
}

.card {
    border: 1px solid #ccc;
    border-radius: 10px;
    padding: 16px;
    margin-bottom: 16px;
    background: #fff;
}

.log__card {
    border: 1px solid #ccc;
    padding: 16px;
    margin-bottom: 16px;
    background: #fff;
}

.right-panel {
    width: 40%;
}

.fact {
    color: black;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    margin-bottom: 8px;
}
</style>