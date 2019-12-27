<template>
    <div class="display">
       {{displayValueFormated}}
    </div>
</template>

<script>
export default {
    props: {
        displayValue: String
    },
    computed: {
        displayValueFormated() {
            return this.displayValue.replace('**','^').replace('*','x');
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