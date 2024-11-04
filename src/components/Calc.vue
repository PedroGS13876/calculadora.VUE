<script setup>
import { reactive } from 'vue';

const estado = reactive({
    digitacao: '', // Armazenará a fórmula completa
    display: '0', // Exibe o valor ou fórmula
});

// Função para atualizar a exibição e concatenar números e operadores
const atualizarDisplay = (valor) => {
    // Se o display atual for '0', substitui pelo novo valor, caso contrário, concatena
    if (estado.digitacao === '0' || estado.display === '0') {
        estado.digitacao = valor.toString();
    } else {
        estado.digitacao += valor.toString(); // Concatena o valor
    }
    estado.display = estado.digitacao; // Atualiza o 'display'
};

// Função para calcular a fórmula
const calcularResultado = () => {
    try {
        // Calcula o resultado usando eval() (ou uma alternativa mais segura)
        const resultado = eval(estado.digitacao);
        estado.display = resultado.toString(); // Exibe o resultado
        estado.digitacao = resultado.toString(); // Armazena o resultado para futuras operações
    } catch (error) {
        estado.display = 'Erro'; // Se houver erro na fórmula
        estado.digitacao = ''; // Limpa a fórmula
    }
};
// Limpa tudo digitado ate o momento 
const limpaDisplay = () => {
    estado.digitacao = '0';
    estado.display = 0;
}
</script>

<template>
    <section class="display">
        <input type="text" class="presenter" :value="estado.display" readonly />
    </section>
    <section class="keyboard">
        <div class="line-1 lines">
            <button @click="atualizarDisplay(7)">7</button>
            <button @click="atualizarDisplay(8)">8</button>
            <button @click="atualizarDisplay(9)">9</button>
            <button @click="atualizarDisplay(0)">0</button>
        </div>
        <div class="line-2 lines">
            <button @click="atualizarDisplay(4)">4</button>
            <button @click="atualizarDisplay(5)">5</button>
            <button @click="atualizarDisplay(6)">6</button>
            <button @click="atualizarDisplay('.')">,</button>
        </div>
        <div class="line-3 lines">
            <button @click="atualizarDisplay(1)">1</button>
            <button @click="atualizarDisplay(2)">2</button>
            <button @click="atualizarDisplay(3)">3</button>
            <button @click="calcularResultado">Enter</button>
        </div>
        <div class="line-4 lines">
            <button @click="atualizarDisplay('/')">/</button>
            <button @click="atualizarDisplay('*')">*</button>
            <button @click="atualizarDisplay('-')">-</button>
            <button @click="atualizarDisplay('+')">+</button>
        </div>
        <div class="line-5">
            <button @click="limpaDisplay()">Limpar</button>
        </div>
    </section>
</template>

<style scoped>
.display {
    margin-top: 15px;
}

.presenter {
    background-color: #fff;
    height: 40px;
    border-radius: 8px;
    padding: 5px;
    padding-left: 40px;
    font-size: 40px;
    width: calc(100% - 40px);
}

input {
    box-shadow: 4px 4px 4px #9c9c9c;
}

.keyboard {
    margin-top: 65px;
}

.lines {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    gap: 15px;
    margin-bottom: 15px;
}

.lines button {
    color: #00000077;
    height: 50px;
    font-size: 30px;
    border-radius: 15px;
}

.line-5 button {
    width: 100%;
    height: 80px;
    font-size: 45px;
    border-radius: 15px;
    margin: 5px;
    margin-top: 15px;
}
</style>