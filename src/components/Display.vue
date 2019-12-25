<template>
    <div class="display">
       {{displayText}}
    </div>
</template>

<script>
export default {
    data() {
        return {
            displayText: ''
        }
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