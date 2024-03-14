<template>
    <div class="calculator">
        <div class="head">
            <input type="text" v-model="result" disabled/>
        </div>
        <div class="buttons">
            <div class="buttonsRow">
                <button @click="appendToDisplay('7')">7</button>
                <button @click="appendToDisplay('8')">8</button>
                <button @click="appendToDisplay('9')">9</button>
                <button @click="deleteLast()" class="blue">DEL</button>
            </div>
            <div class="buttonsRow">
                <button @click="appendToDisplay('4')">4</button>
                <button @click="appendToDisplay('5')">5</button>
                <button @click="appendToDisplay('6')">6</button>
                <button @click="appendToDisplay('+')">+</button>
            </div>
            <div class="buttonsRow">
                <button @click="appendToDisplay('1')">1</button>
                <button @click="appendToDisplay('2')">2</button>
                <button @click="appendToDisplay('3')">3</button>
                <button @click="appendToDisplay('-')">-</button>
            </div>
            <div class="buttonsRow">
                <button @click="appendToDisplay('.')">.</button>
                <button @click="appendToDisplay('0')">0</button>
                <button @click="appendToDisplay('/')">/</button>
                <button @click="appendToDisplay('*')">x</button>
            </div>
            <div class="buttonsRow">
                <button @click="clear()" class="blue">RESET</button>
                <button @click="calculate()" class="red">=</button>
            </div>
        </div>
    </div>
</template>
<script>
    export default{
        data(){
            return{
                result: ''
            }
        },
        methods: {
            appendToDisplay(value) {
                const lastChar = this.result[this.result.length - 1];
                if(value === "+" || value === "-" || value === "*" || value === "/"){
                    if(["+","-","*","/"].includes(lastChar)){
                        this.result = this.result.slice(0, -1) + value;
                    }
                    else{
                        this.result += value;
                    }
                }
                else{
                    this.result += value;
                }
            },
            clear() {
                this.result = '';
            },
            calculate() {
                try {
                    this.result = eval(this.result);
                } 
                catch(error) {
                    this.result = 'Error';
                }
            },
            deleteLast() {
                this.result = this.result.slice(0, -1);
            }
        }
    }
</script>
<style scoped>
    .calculator{width: 400px;}
    .head{float:left;width:100%;background:#333;border-radius:5px;padding:20px;margin-bottom:10px;}
    .head input{float:left;width:100%;background:none;border:0;height:50px;border-radius:5px;font-size:18px;font-weight:bold;text-align:right;font-size: 28px;color:#fff;}
    .buttonsRow{float:left;width:100%;display:flex;column-gap:20px;}
    .buttons{float:left;width:100%;display:flex;flex-direction:column;row-gap:20px;background:#333;padding:20px;border-radius:5px;}
    .buttonsRow button{float:left;width:100%;height:40px;border-radius:5px;background:#fff;font-size:18px;font-weight:bold;}
    .buttonsRow button.blue{background-color: rgb(101 113 153);color:#fff;}
    .buttonsRow button.red{background-color: rgb(209 63 48);color:#fff;}
</style>