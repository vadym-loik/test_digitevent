<template>
    <div>
        <div class="container">
            <div class="left-panel">
                <div class="card">
                    <h3>A cool <span>Maths</span> fact</h3>
                    <Button class="btn" @click="fetchMathFact" />
                    <p class="card__text">{{ mathFact }}</p>

                </div>
                <div class="card">
                    <h3>A cool <span>Date</span> fact</h3>
                    <Button class="btn" @click="fetchDateFact" />
                    <p class="card__text">{{ dateFact }}</p>

                </div>
            </div>
            <div class="right-panel">
                <div class="log__card">
                    <h3><span>Logs</span></h3>
                    <ul>
                        <p v-if="mathFact" class="log__title">Math Fact</p>
                        <li class="mathFact" v-for="fact in mathFactLog" :key="fact">{{ fact }}</li>
                    </ul>
                    <ul>
                        <p v-if="dateFact" class="log__title">Date Fact</p>
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
import Button from './Button.vue';

const mathFact = ref('');
const dateFact = ref('');
// const timestamp = ref('');

const mathFactLog = ref<string[]>([]);
const dateFactLog = ref<string[]>([]);

// timestamp.value = new Date().toLocaleString();

const fetchMathFact = async () => {
    try {
        const response = await axios.get('http://numbersapi.com/random/math');
        const fact = response.data;
        const timestamp = new Date().toLocaleString();

        mathFact.value = fact;
        mathFactLog.value.push(timestamp, fact);

        console.log(mathFactLog.value);

    } catch (error) {
        console.error(error);
    }
};

const fetchDateFact = async () => {
    try {
        const response = await axios.get('http://numbersapi.com/random/date');
        const fact = response.data;
        const timestamp = new Date().toLocaleString();

        dateFact.value = fact;
        dateFactLog.value.push(timestamp, fact);
    } catch (error) {
        console.error(error);
    }
};
</script>

<style lang="scss" scoped>
@import '../assets/scss/variables.scss';


h3 {
    font-weight: 400;
    margin-bottom: 20px;
}

span {
    font-weight: 600;
    text-decoration: underline;
}

.app {
    background: #F4F4F4;
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
    position: relative;
    box-shadow: 1px 7px 5px 0px rgba(0, 0, 0, 0.17);

    &__text {
        font-weight: 600;
        color: black;
    }
}

.btn {
    position: absolute;
    right: 20px;
    top: 20px;
}

.log__title {
    color: black;
    font-weight: 600;
}

.timestamp {
    font-weight: 600;
    color: black;
}

.log__card {
    border: 1px solid #ccc;
    padding: 16px;
    margin-bottom: 16px;
    background: #fff;
    height: 100%;
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