<template>
  <div class="hello">
    <div class="">
      <h1>
        <u style="font-family: san-serif; font-size:30px">
          <b>Quotes</b>
        </u>
        <sup style="font-family: serif; font-style: italic; font-size: 30px"><b>&ldquo;&rdquo;</b></sup>
      </h1>
      <p style="font-size: 25px">
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
export default {
  name: 'HelloWorld',
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
  background-color: rgb(219, 208, 208);
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 80%;
  padding: 76px;
}
</style>
