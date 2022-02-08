<template>
  <div class=" bg-gray-300 grid place-items-center w-4/5 p-20 mx-auto my-auto">
    <div>
      <Header class="p-4" title="Quotes"/>
      <p class="text-2xl">
        <b>
          {{ quotes.text }}
        </b>
      </p>
      <p style="font-size: 18px">
        <b>
          {{ quotes.author? `-- ${quotes.author}` : '' }}
        </b>
      </p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Header from './Header.vue'
export default {
  name: 'HelloWorld',
  components: {
    Header
  },
  data() {
    return {
      quotes: '',
      author: ''
    }
  },
  created() {
    axios.get('https://type.fit/api/quotes')
    .then((response) => {
        const min = 0;
        const max = Object.keys(response.data).length;

        setInterval(() => {
          const index = Math.floor(Math.random() * (max - min)) + min; 
          this.quotes = response.data[index]
        }, 10000)
    })
    .catch((err)=> {
      console.log(err)
    })
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  /* background-color: rgb(219, 208, 208); */
  /* position: fixed; */
  /* top: 50%;
  left: 50%;
  transform: translate(-50%, -50%); */
  /* width: 80%; */
  /* padding: 76px; */
}
</style>
