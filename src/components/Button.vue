<template>
    <div>
        <button :class="{operation, clear, number, symbol, result}" class="button">{{value}}</button>
    </div>
</template>

<script>
export default {
    props: {
        operation: Boolean,
        clear: Boolean,
        number: Boolean,
        symbol: Boolean,
        result: Boolean,
        value: [String, Number]
    }
}
</script>

<style scoped>
    .button{
        border-width: 1px;
        border-color: rgba(255, 255, 255, 0.1);
        border-style: solid;
        display: flex;
        align-items: center;
        justify-content: center;
        height: 50px;
        width: 50px;
        padding: 10px;
        font-size: 1.2em;
        color: white;
        border-radius: 50%;
    }
    .button:hover {
        filter: brightness(120%);
        border-color: rgba(255, 255, 255, 0.527)
    }
    .number{
        background-color: #161638;
    }
    .symbol{
        background-color: #161638;
    }
    .clear{
        background-color: #27275b;
    }
    .operation{
       background-color: orange;
    }
    .result{
       background-color: rgb(228, 65, 65);
    }
</style>