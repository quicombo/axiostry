<template>
    <div class="overlay">
        <h1>lets do some image</h1>
         <div>
        <div class="card_wrapper" style="">
           <div class="card" v-for="item in list" :key="item.id">
            <div class="header">
                image ID:{{ item.id }}
            </div>
            <div class="author">
                image author: {{ item.author }}
            </div>
            <div class="image">
                <img :src=item.download_url alt="">
            </div>
            </div> 
        </div>
    </div>
    </div>   
</template>
<script>
import axios from 'axios'
export default {
    name: 'imageGet',
    data () {
        return {
            list: null
        }
    },
    mounted () {
        axios
        .get('https://picsum.photos/v2/list')
        .then ( response => (this.list = response.data))
    }    
}
</script>
<style scoped>
.overlay {
    background-color: rgba(0,0,0,.3);
}
.card_wrapper {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
}
.card{
    margin: 10px;
    background-color: rgba(0,0,0,.4);    
}
.header {
    color: white;
    font-weight: bold;
    text-transform: uppercase;
    padding: 15px 0; 
}
.author {
    font-size: 12px;
    color: white;
    margin-bottom: 15px;
}
.image img{
    max-width: 250px;
    height: auto;
}
</style>