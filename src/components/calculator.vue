<template>
<div class="min-h-screen bg-gray-700 flex items-center justify-center">
    <div class="w-11/12">
        <div class="bg-gray-800 border-2 border-gray-900 shadow-2xl rounded-lg">
            <p class="font-semibold text-gray-500 h-6">{{getOperacion}}</p>
            <p class="font-bold text-3xl text-white my-4">{{getResultado}}</p>
        </div>
        <div class="p-6 text-gray-800 grid grid-cols-4 gap-4 text-xl">
            <button class="font-mono col-span-3 bg-blue-500 hover:bg-blue-400 rounded-full p-5" @click="clickAC()">AC</button>
            <button class="font-mono bg-purple-500 hover:bg-purple-400 rounded-full p-5" @click="clickDEL()">DEL</button>
            <button class="font-mono bg-purple-500 hover:bg-purple-400 rounded-full p-5" @click="click('÷')">÷</button>

            <button class="font-mono bg-gray-500 hover:bg-gray-400 rounded-full p-5" @click="click('7')">7</button>
            <button class="font-mono bg-gray-500 hover:bg-gray-400 rounded-full p-5" @click="click('8')">8</button>
            <button class="font-mono bg-gray-500 hover:bg-gray-400 rounded-full p-5" @click="click('9')">9</button>
            <button class="font-mono bg-purple-500 hover:bg-purple-400 rounded-full p-5" @click="click('x')">x</button>

            <button class="font-mono bg-gray-500 hover:bg-gray-400 rounded-full p-5" @click="click('4')">4</button>
            <button class="font-mono bg-gray-500 hover:bg-gray-400 rounded-full p-5" @click="click('5')">5</button>
            <button class="font-mono bg-gray-500 hover:bg-gray-400 rounded-full p-5" @click="click('6')">6</button>
            <button class="font-mono bg-purple-500 hover:bg-purple-400 rounded-full p-5" @click="click('-')">-</button>

            <button class="font-mono bg-gray-500 hover:bg-gray-400 rounded-full p-5" @click="click('1')">1</button>
            <button class="font-mono bg-gray-500 hover:bg-gray-400 rounded-full p-5" @click="click('2')">2</button>
            <button class="font-mono bg-gray-500 hover:bg-gray-400 rounded-full p-5" @click="click('3')">3</button>
            <button class="font-mono bg-purple-500 hover:bg-purple-400 rounded-full p-5" @click="click('+')">+</button>

            <button class="font-mono bg-gray-500 hover:bg-gray-400 rounded-full p-5" @click="click('0')">0</button>
            <button class="font-mono bg-purple-500 hover:bg-purple-400 rounded-full p-5" @click="click('.')">.</button>
            <button class="font-mono bg-purple-500 hover:bg-purple-400 rounded-full p-5"  @click="clickResultado()">=</button>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: 'Calculadora',
    data(){
        return{
            getOperacion: '',
            getResultado: '0',
        }
    },
    methods:{
        clickAC(){
            this.getResultado = '0';
        },
        clickDEL(){
            if(this.getResultado.length > 1){
                this.getResultado = this.getResultado.substring(0,this.getResultado.length - 1);
            }else{
                this.getResultado = '0';
            }
        },
        click(num){
            if(this.getResultado === '0'){
                this.getResultado = num;
            }else{
                this.getResultado += num;
            }
        },
        clickResultado(){
            let operacion = this.getResultado;
            this.getOperacion = operacion;

            operacion = operacion.replace('x', '*');
            operacion = operacion.replace('÷', '/');
            this.getResultado = eval(operacion);
        }
    }
}
</script>

<style scoped>
button{
  
}

</style>