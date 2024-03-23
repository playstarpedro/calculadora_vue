<script setup>
import { reactive } from 'vue';
const props = defineProps(['pNum1', 'pNum2', 'pOperacao', 'pCalcular']);

const estado = reactive({
    num1: 0,
    num2: 0,
    operacao: '+',
})

function calcular(num1, num2, operacao) {
    num1 = Number(num1);
    num2 = Number(num2);

    switch (operacao) {
        case '+': return num1 + num2;
        case '-': return num1 - num2;
        case '*': return num1 * num2;
        case '÷': return num1 / num2;
        default: return null
    }
};
</script>

<template>
    <div class="container text-center p-2">
        <form>
            <div class="row">
                <div class="col-4">
                    <input @keyup="evento => estado.num1 = evento.target.value" class="m-2 form-control text-center"
                        type="number" placeholder="primeiro número" required>
                </div>
                <div class="col-4">
                    <input @keyup="evento => estado.num2 = evento.target.value" class="m-2 form-control text-center"
                        type="number" placeholder="primeiro número" required>
                </div>
                <div class="col-4">
                    <select @change="evento => estado.operacao = evento.target.value"
                        class="m-2 form-control text-center text-white bg-warning">
                        <option>+</option>
                        <option>-</option>
                        <option>*</option>
                        <option>÷</option>
                    </select>
                </div>
            </div>
        </form>
        <div class="m-2">
            <h3>Resultado: {{ calcular(estado.num1, estado.num2, estado.operacao) }}</h3>
        </div>
    </div>
</template>