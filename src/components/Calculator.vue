<template>
    <div class="centralize-content">
        <div class="calculator">
            <Label />
            <div class="flex-row-around">
                <Display />
            </div>
            <div class="flex-row-around">
                <Button clear value="C"/>
                <Button value="(" symbol />
                <Button value=")" symbol />
                <Button value="/" operation />
            </div>
             <div class="flex-row-around">
                <Button number v-for="i of 3" :key="i+7" :value="i+6"/>
                <Button operation value="-"/>
            </div>
            <div class="flex-row-around">
                <Button number v-for="i of 3" :key="i" :value="i"/>
                <Button operation value="+"/>
            </div>
            <div class="flex-row-around">
                <Button number v-for="i of 3" :key="i+4" :value="i+3"/>
                <Button operation value="X"/>
            </div>
            <div class="flex-row-around">
                <Button symbol value="%" />
                <Button number :value="0"/>
                <Button symbol value="."/>
                <Button result value="="/>
            </div>
        </div>
    </div>
</template>

<script>
import Label from './Label'
import Button from './Button'
import Display from './Display'

export default {
    components: {
        Button, Display, Label
    }, 
    
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
        max-width: 350px;
        border-radius: 10px;
    }
</style>