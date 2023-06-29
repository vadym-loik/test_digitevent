<template>
    <div class="app">
        <div class="left-panel">
            <div class="card">
                <h2>A cool Maths fact</h2>
                <p>{{ mathFact }}</p>
                <i class="ri-arrow-down-circle-line" @click="fetchMathFact"></i>
            </div>
            <div class="card">
                <h2>A cool Date fact</h2>
                <p>{{ dateFact }}</p>
                <i class="ri-arrow-down-circle-line" @click="fetchDateFact"></i>
            </div>
        </div>
        <div class="right-panel">
            <div class="card">
                <h2>Logs</h2>
                <ul>
                    <li class="fact" v-for="fact in factLog" :key="fact">{{ fact }}</li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import axios, { AxiosResponse } from 'axios';

const mathFact = ref('');
const dateFact = ref('');
const factLog = ref<string[]>([]);

console.log(factLog.value);


interface FactResponse {
    data: string;
}

const fetchMathFact = async () => {
    try {
        const response: AxiosResponse<FactResponse> = await axios.get('http://numbersapi.com/random/math');

        // console.log(response);

        mathFact.value = response.data.data;
        // console.log(mathFact.value);

        factLog.value.push(mathFact.value);
    } catch (error) {
        console.error(error);
    }
};

const fetchDateFact = async () => {
    try {
        const response: AxiosResponse<FactResponse> = await axios.get('http://numbersapi.com/random/date');

        // console.log(response);

        dateFact.value = response.data.data;
        // console.log(dateFact.value);

        factLog.value.push(dateFact.value);
    } catch (error) {
        console.error(error);
    }
};
</script>

<style lang="scss" scoped>
@import '../assets/scss/variables.scss';

.app {
    background: grey;
    display: flex;
    justify-content: space-between;
}

.left-panel {
    width: 50%;
}

.card {
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