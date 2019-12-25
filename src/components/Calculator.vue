<template>
    <div class="centralize-content">
        <div class="calculator">
            <Label />
            <div class="flex-row-around">
                <Display :displayValue="displayValue"/>
            </div>
            <div class="flex-row-around">
                <Button clear value="C" v-on:click.native="clear()"/>
                <Button value="(" symbol v-on:click.native="addDigit('(')" />
                <Button value=")" symbol v-on:click.native="addDigit(')')" />
                <Button value="/" operation v-on:click.native="addDigit('/')" />
            </div>
             <div class="flex-row-around">
                <Button number v-for="i of 3" :key="i+6" :value="i+6" v-on:click.native="addDigit(i+6)" />
                <Button operation value="-" v-on:click.native="addDigit('-')" />
            </div>
            <div class="flex-row-around">
                <Button number v-for="i of 3" :key="i" :value="i" v-on:click.native="addDigit(i)"/>
                <Button operation value="+" v-on:click.native="addDigit('+')" />
            </div>
            <div class="flex-row-around">
                <Button number v-for="i of 3" :key="i+3" :value="i+3" v-on:click.native="addDigit(i+3)" />
                <Button operation value="X" v-on:click.native="addDigit('X')" />
            </div>
            <div class="flex-row-around">
                <Button symbol value="%" v-on:click.native="addDigit('%')" />
                <Button number :value="0" v-on:click.native="addDigit(0)" />
                <Button symbol value="." v-on:click.native="addDigit('.')" />
                <Button result value="=" />
            </div>
        </div>
    </div>
</template>

<script>
import Label from './Label'
import Button from './Button'
import Display from './Display'

export default {
    data() {
        return {
            displayValue: '0'
        }
    },
    components: {
        Button, Display, Label
    }, 
    methods: {
        clear() {
            this.displayValue = '0';
        },
        addDigit(value) {
            value = String(value);
            this.displayValue = this.displayValue == '0' ? value : this.displayValue + value; 
        }
    }
}
</script>

<style scoped>
    div.calculator{
        margin-top: 10px;
        display: flex;
        justify-content: space-around;
        flex-direction: column;
        background-color: #131232;
        width: 100%;
        height: 420px;
        max-width: 330px;
        border-radius: 10px;
    }
</style>