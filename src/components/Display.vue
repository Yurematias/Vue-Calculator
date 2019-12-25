<template>
    <div class="display">
       {{displayValue}}
    </div>
</template>

<script>
export default {
    props: {
        displayValue: String
    },
    updated() {
        this.displayText+=this.newElement;
    }
}
</script>

<style scoped>
    .display{
        height: 12px;
        font-family: monospace;
        font-size: 1.5rem;
        align-items: center;
        width: 100%;
        padding: 15px;
        color: white;
        display: flex;
        justify-content: right;
        background-color: #02030e;
    }
</style>