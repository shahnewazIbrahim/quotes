<template>
  <div class="grid place-items-center w-4/5 p-20 mx-auto  h-80">
    <div @mouseover="offApi" @mouseleave="apiCall(dataResponse)" class="overflow-hidden cursor-pointer">
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
      author: '',
      intervalFunc: undefined,
      dataResponse : ''
    }
  },
  created() {
    axios.get('https://type.fit/api/quotes')
    .then((response) => {
      this.dataResponse = response
        this.apiCall(response)
    })
    .catch((err)=> {
      console.log(err)
    })
  },
  methods : {
    apiCall(response) {
      const min = 0;
        const max = Object.keys(response.data).length;

       this.intervalFunc =  setInterval(() => {
          const index = Math.floor(Math.random() * (max - min)) + min; 
          this.quotes = response.data[index]
        }, 10000)
    },
    offApi() {
      clearInterval(this.intervalFunc)
    }
  }
}
</script>