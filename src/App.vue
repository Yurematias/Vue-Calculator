<template>
   <div>
        <Calculator />
        <Footer />
   </div>
</template>

<script>
import Calculator from './components/Calculator'
import Footer from './components/Footer'

export default {
    components: {
        Calculator, Footer
    }
}
</script>

<style>
.centralize-content{
    display: flex;
    justify-content: center;
}

body{
    font-family: 'Roboto', sans-serif;
    background-color: gainsboro;
}

.flex-center-vertical{
    display: flex;
    justify-content: center;
    flex-direction: column;
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