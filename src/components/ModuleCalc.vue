<template>
    <div class="calculator-container">
        <div class="calculator">
            <h1 class="title">CALC VUE</h1>
            <div class="display">
                <input class="display-input" type="text" v-model="display" readonly>
            </div>
            <div class="buttons">
                <button @click="add">+</button>
                <button @click="subtract">-</button>
                <button @click="multiply">*</button>
                <button @click="divide">/</button>
                <button @click="clear">C</button>
                <button @click="percent">%</button>
                <button @click="decimal">.</button>
                <button @click="number(1)">1</button>
                <button @click="number(2)">2</button>
                <button @click="number(3)">3</button>
                <button @click="number(4)">4</button>
                <button @click="number(5)">5</button>
                <button @click="number(6)">6</button>
                <button @click="number(7)">7</button>
                <button @click="number(8)">8</button>
                <button @click="number(9)">9</button>
                <button @click="number(0)">0</button>
                <button @click="equals">=</button>
                <button @click="calculate('^')">^</button>
                <button @click="calculate('sqrt')">√</button>
                <button @click="calculate('sin')">sin</button>
                <button @click="calculate('cos')">cos</button>
                <button @click="calculate('tan')">tan</button>
                <button @click="calculate('log')">log</button>
                <button @click="calculate('ln')">ln</button>
                <button @click="calculate('e')">e</button>
                <button @click="calculate('pi')">π</button>
                <button @click="calculate('(')">(</button>
                <button @click="calculate(')')">)</button>
                <button class="enter" @click="enter">GO</button>
                <button class="space" @click="space">|</button>
                <button class="backspace" @click="backspace">DEL</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            display: '0',
            error: ''
        }
    },
    methods: {
        add() {
            this.calculate(' + ');
        },
        subtract() {
            this.calculate(' - ');
        },
        multiply() {
            this.calculate(' * ');
        },
        divide() {
            this.calculate(' / ');
        },
        clear() {
            this.display = '0';
        },
        percent() {
            this.calculate(' % ');
        },
        decimal() {
            if (this.display.includes('.')) return;
            this.display += '.';
        },
        number(num) {
            if (this.display === '0') this.display = '';
            this.display += num;
        },
        equals() {
            try {
                this.display = eval(this.display).toString();
            } catch (e) {
                this.error = 'Expressao invalida';
                this.display = this.error;
            }
        },
        enter() {
            this.equals();
        },
        space() {
            this.display +='';
        },
        backspace() {
            this.display = this.display.slice(0, -1);
            if (this.display === '') this.display = '0';
        },
        calculate(operator) {
            if (this.display.endsWith(operator)) return;
            if (this.display === '0') this.display = '';
            this.display += operator;
        }
    }
}
</script>

<style scoped>
.calculator-container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background: linear-gradient(135deg, #6a0dad, #ff8c00);
}

.calculator {
    background-color: #2a1b3d;
    padding: 20px;
    border-radius: 15px;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
    width: 300px;
}

.title {
    text-align: center;
    color: #fff;
    font-size: 2.5rem;
    font-weight: bold;
    margin-bottom: 20px;
}

.display {
    width: 100%;
    height: 60px;
    display: flex;
    align-items: center;
    justify-content: flex-end;
    border-radius: 10px;
    overflow: hidden;
    margin-bottom: 20px;
}

.display-input {
    width: 100%;
    height: 100%;
    padding: 0 15px;
    border: none;
    background-color: #5e1187;
    font-size: 30px;
    font-weight: bold;
    color: #fff;
    text-align: right;
    border-radius: 10px;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
}

button {
    width: 60px;
    height: 60px;
    background-color: #7a39b5;
    color: white;
    font-size: 20px;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    transition: background-color 0.3s, transform 0.1s;
}

button:hover {
    background-color: #9b48d2;
    transform: scale(1.05);
}

button:active {
    transform: scale(0.95);
}

.error {
    color: red;
    font-size: 18px;
    text-align: center;
    margin-top: 10px;
}
.enter {
    background-color: rgb(61, 135, 61);
}
.space {
    background-color: #4e4a4a;
}
.backspace {
    background-color: #ac3333;   
}
</style>
