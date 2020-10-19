<template>
  <div class="hello">
    <H1>Hello</H1>
    <div v-if="errored">Ошибка получения данных</div>
    <div v-else>
      Курс BITCOIN
    <div v-if="loading">Загрузка</div>
    <div v-else v-for="currency in info" :key="currency.id">
      {{ currency.description }}
      <span v-html="currency.symbol"></span>{{ currency.rate_float | currencydecimal }}
    </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {  
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data () {
    return {
      info: null,
      loading: true,
      errored: false
    }
  },
  mounted () {
    axios
    .get ('https://api.coindesk.com/v1/bpi/currentprice.json')
    .then ( response => (this.info = response.data.bpi))
    .catch(error => {
      console.log(error)
      this.errored = true
    })
    .finally( () => this.loading = false)
  },
  filters: {
  currencydecimal (value) {
    return value.toFixed(2)
  }
},
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  background-color: rgba(0,0,0,.3);
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
