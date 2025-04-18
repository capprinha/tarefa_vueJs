<script setup>
import { computed, reactive } from 'vue';
    const estado = reactive({
        num1: 0,
        num2: 0,
        operacao: '',
    })
    const resultado = computed(()=>{
        const n1 = parseFloat(estado.num1)
        const n2 = parseFloat(estado.num2)

        switch(estado.operacao){
            case 'soma':
                return n1 + n2
            case 'subtracao':
                return n1 - n2
            case 'divicao':
                if(n2 == 0){
                    return 'Divisão por zero'
                }
                else{
                    return n1 / n2
                }
            case 'multiplicacao':
                return n1 * n2
            default:
                return 'Selecione uma operação'
        }
    })
    
    

    
    
</script> 

<template>
    <main>
        <form @submit.prevent>
            <input type="number" @keyup="evento => estado.num1 = evento.target.value" placeholder="Digite o primeiro número">
            <input type="number" @keyup="evento => estado.num2 = evento.target.value" placeholder="Digite o segundo número">
            <select v-model="estado.operacao">
                <option value="subtracao">-</option>
                <option value="soma">+</option>
                <option value="multiplicacao">x</option>
                <option value="divicao">:</option>
            </select>
        </form>
        <h3>
            O resultado é: {{resultado }}
        </h3>
    </main>
</template>

<style scoped>
main{
    max-width: 600px;
    width: 100%;
    margin: 0 auto;
    background-color: #ccc;
}
form{
    display: flex;
    align-items: center;
    justify-content: space-around;
}
input, select, h3{
    padding: 5px;
    text-align: center;
}
</style>