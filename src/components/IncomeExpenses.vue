<template>
    <div class="inc-exp-container">
        <div>
            <h4>Income</h4>
            <p id="money-plus" class="money plus">${{ formattedIncome }}</p>
        </div>
        <div>
            <h4>Expenses</h4>
            <p id="money-minus" class="money minus">${{ formattedExpenses }}</p>
        </div>
    </div>
</template>
<script setup>
import { computed } from 'vue';

const props = defineProps({
    income: {
        type: Number,
        required: true,
    },

    expenses: {
        type: Number,
        required: true,
    },
});

const formattedIncome = computed(() => {
    if (props.income >= 1000000000) {
        return props.income.toExponential(2);
    }
    return props.income.toFixed(2);
});

const formattedExpenses = computed(() => {
    if (props.expenses <= -1000000000) {
        return props.expenses.toExponential(2);
    }
    return props.expenses.toFixed(2);
});
</script>