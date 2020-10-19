<template>
    <div class="wrapper">
        chuck jokes
        <div class="joke">
            <button @click="getJoke ()">get joke</button>
            <div v-if="joke">{{ joke.data.value.joke }}</div>
        </div>
    </div>    
</template>
<script>
import axios from 'axios'
export default {
    name: 'chuck',
    data () {
        return {
            joke: null
        }
    },
    methods: {
        getJoke () {
        axios
        .get('https://api.icndb.com/jokes/random')
        .then( response => {
            this.joke = response
        })                
        }        
    }    
}
</script>
<style scoped>
.wrapper {
    margin-top: 20px;
    font-size: 20px;
    font-weight: 600;
}
button { 
    background-color:bisque
}
</style>