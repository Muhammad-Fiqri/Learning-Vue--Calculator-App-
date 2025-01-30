<script setup lang="ts">
import { ref, watch } from 'vue';
import nerdamer  from 'nerdamer';

const result = ref("");

watch(result, () => {
    console.info(result.value)
})

function handleButton(op:string) {
    if (op == "=") {
        result.value = nerdamer(result.value).text()
    } else {
        result.value += op
    }
} 

const operands = ref(["1","2","3","4","5","6","7","8","9","0","-","+","/","*","="])
</script>

<template>
    <div id="calculator-box">
        <div id="calculator">
            <input v-model="result" type="text" name="screen" id="screen">
            <div id="buttons-box">
                <button v-for="operand in operands" @click="handleButton(operand)">
                    {{ operand }}
                </button>
            </div>
        </div>
    </div>
</template>

<style scoped>
    #calculator-box {
        width: 100vw;
        height: 93vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    #calculator {
        width: 40vw;
        height: 90%;
        background-color: gray;
        border-radius: 10px;

        padding: 10px;
    }

    #buttons-box {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-template-rows: 1fr 1fr 1fr 1fr 1fr;
        height: 80%;
    }

    #screen {
        width: 100%;
        height: 20%;
    }

    #screen::-webkit-outer-spin-button,
    #screen::-webkit-inner-spin-button {
        -webkit-appearance: none;
        margin: 0;
    }

    /* Firefox */
    #screen {
        -moz-appearance: textfield;
    }
</style>
