<template>
  <div class="bg-gray-300 grid place-items-center w-4/5 p-20 mx-auto h-80">
    <div
      @mouseover="offApi"
      @mouseleave="apiCall(dataResponse)"
      class="overflow-hidden cursor-pointer"
    >
      <Header class="p-4" title="Quotes" />
      <p class="text-2xl">
        <b>
          {{ quotes.text }}
          <!-- {{ quotes }} -->
        </b>
      </p>
      <p style="font-size: 18px">
        <b>
          {{ quotes.author ? `-- ${quotes.author}` : "" }}
        </b>
      </p>
    </div>
  </div>
</template>

<script>
// import axios from "axios";
import Header from "./Header.vue";
export default {
  name: "HelloWorld",
  components: {
    Header,
  },
  data() {
    return {
      quotes: "",
      author: "",
      intervalFunc: undefined,
      dataResponse: "",
      response: {
        data:
          // {
          [
            {
              text: "You have to write the book that wants to be written. And if the book will be too difficult for grown-ups, then you write it for children.",
              author: "Madeleine L'Engle",
            },
            {
              text: "If you don't have time to read, you don't have the time (or the tools) to write. Simple as that.",
              author: "Stephen King",
            },
            {
              text: "We write to taste life twice, in the moment and in retrospect.",
              author: "Anaïs Nin",
            },
            {
              text: "Substitute 'damn' every time you're inclined to write 'very;' your editor will delete it and the writing will be just as it should be.",
              author: "Mark Twain",
            },
            {
              text: "If there's a book that you want to read, but it hasn't been written yet, then you must write it.",
              author: "Toni Morrison",
            },
          ],
        // },
      },
    };
  },
  created() {
    this.dataResponse = this.response;
    this.apiCall(this.response);

    // axios
    //   .get("https://type.fit/api/quotes")
    //   .then((response) => {
    //     this.dataResponse = response;
    //     this.apiCall(response);
    //   })
    //   .catch((err) => {
    //     console.log(err);
    //   });
  },
  methods: {
    apiCall(response) {
      const min = 0;
      const max = Object.keys(response.data).length;
      console.log(Math.floor(Math.random() * (max - min)) + min);
      this.intervalFunc = setInterval(() => {
        const index = Math.floor(Math.random() * (max - min)) + min;
        this.quotes = response.data[index];
      }, 10000);
    },
    offApi() {
      clearInterval(this.intervalFunc);
    },
  },
};
</script>
