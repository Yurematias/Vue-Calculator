<template>
    <div class="centralize-content">
        <div class="calculator">
            <Label />
            <div class="flex-row-around">
                <Display :displayValue="displayValue"/>
            </div>
            <div class="flex-row-around">
                <Button clear value="C" v-on:click.native="clear()"/>
                <Button value="^" symbol v-on:click.native="addDigit('**')" />
                <Button value="del" symbol v-on:click.native="overrideLastNumber('')" />
                <Button value="/" operation v-on:click.native="addDigit('/')" />
            </div>
             <div class="flex-row-around">
                <Button number v-for="i of 3" :key="i+6" :value="i+6" v-on:click.native="addDigit(i+6)" />
                <Button operation value="-" v-on:click.native="addDigit('-')" />
            </div>
            <div class="flex-row-around">
                <Button number v-for="i of 3" :key="i+3" :value="i+3" v-on:click.native="addDigit(i+3)" />
                <Button operation value="+" v-on:click.native="addDigit('+')" />
            </div>
            <div class="flex-row-around">
                <Button number v-for="i of 3" :key="i" :value="i" v-on:click.native="addDigit(i)"/>
                <Button operation value="x" v-on:click.native="addDigit('*')" />
            </div>
            <div class="flex-row-around">
                <Button github />
                <Button number :value="0" v-on:click.native="addDigit(0)" />
                <Button symbol value="." v-on:click.native="addDigit('.')" />
                <Button result value="=" v-on:click.native="showResult" />
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
            displayValue: '0',
            displayHaveResult: false
        }
    },
    beforeCreate() {
        // adapting the split method to work with multiple separators
        String.prototype.customSplit = function(...separators) {
            let newString = this;
            for(let i = 0; i < separators.length; i++) {
                newString = newString.split(separators[i]).join(',');
            }
            return newString.split(',');
        }
    },
    components: {
        Button, Display, Label
    }, 
    methods: {
        clear() {
            this.displayValue = '0';
        },
        isOverridable(value) {
            if ((value == '+' || value == '-') && this.displayValue == '0') {
                return true;
            }
            let lastDisplayNumber = this.displayValue.split('')[this.displayValue.length - 1];
            return (this.isSymbol(lastDisplayNumber));
        },
        isSymbol(value) {
            let symbols = ['.','*','+','-','%','/','**'];
            for (const symbol of symbols) {
                if (value == symbol) {
                    return true;
                }
            }
            return false;
        },
        overrideLastNumber(value) {
            this.displayValue = this.displayValue.split('');
            this.displayValue[this.displayValue.length - 1] = value;
            this.displayValue = this.displayValue.join('');
            if (this.displayValue.length == 0) {
                this.displayValue = '0';
            }
        },
        havePointInLastNumber() {
            // return a array with the elements of the string separated by the parameters passed below
            let numbersOfDisplay = this.displayValue.customSplit('-','+','*','%','/');
            let lastDisplayNumber = numbersOfDisplay[numbersOfDisplay.length - 1];

            // if the last number includes a point the user can´t add other point
            return (lastDisplayNumber.includes('.')); 
        },
        addDigit(value) {
            value = String(value);

            if (this.displayHaveResult) {
                this.displayHaveResult = false;
                if (!this.isSymbol(value)) {
                    this.clear();
                    this.overrideLastNumber(value);
                    return;
                }        
            }
            // if the lastNumber is isOverwritable and the number pressed is a sybol
            // or if the display current number is a zero and the number pressed is not a symbol
            if ((this.isOverridable(value) && this.isSymbol(value)) || (this.displayValue == '0' && !this.isSymbol(value))) {
                this.overrideLastNumber(value);    
                return;
            }
            if (value == '.') {
               if (this.havePointInLastNumber()) {
                   return;
               }
            }
            this.displayValue += value;
        }, 
        showResult() {
            this.displayHaveResult = true;
            this.displayValue = String(eval(this.displayValue));
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