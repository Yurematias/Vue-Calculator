<template>
    <Calculator />
</template>

<script>
import Calculator from './components/Calculator'

export default {
    components: {
        Calculator
    }
}
</script>

<style>
.centralize-content{
    display: flex;
    justify-content: center;
}

.flex-row-around{
    display: flex;
    justify-content: space-around;
}

*{
    box-sizing:0; 
    margin:0; 
    padding:0;
}

.text-light{
    color: white;
}
</style>