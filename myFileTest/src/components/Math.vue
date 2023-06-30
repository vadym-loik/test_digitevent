<template>
    <div class="left__panel">
        <div class="card">
            <h3>A cool <span>Maths</span> fact</h3>
            <Button class="btn" @click="fetchMathFact" />
            <p class="card__text">{{ mathFact }}</p>
        </div>

    </div>
</template>

<script setup lang="ts">
import Button from './Button.vue';
import { ref } from 'vue';
import axios from 'axios';

const mathFact = ref('');
const mathFactLog = ref<string[]>([]);

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
// const props = defineProps<{
//     mathFactLog: Object
// }>()

// console.log(props);

</script>

<style scoped>
@import '../assets/scss/variables.scss';

h3 {
    font-weight: 400;
    margin-bottom: 20px;
}

span {
    font-weight: 600;
    text-decoration: underline;
}

.left__panel {
    float: left;
    width: 40%;
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
</style>
