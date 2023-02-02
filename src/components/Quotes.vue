<template>
  <div class="bg-gray-300 grid place-items-center w-4/5 p-20 mx-auto h-80">
    <div
      @mouseover="offApi"
      @mouseleave="apiCall(dataResponse)"
      class="overflow-hidden cursor-pointer"
    >
      <Header class="p-4" title="Quotes" />
      <p class="text-2xl">
        <b class="italic">
          &ldquo; {{ quotes.text }}&rdquo;
          <!-- {{ quotes }} -->
        </b>
      </p>
      <p class="text-lg">
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
            {
              text: "We cannot solve problems with the kind of thinking we employed when we came up with them.",
              author: "Albert Einstein",
            },
            {
              text: "Learn as if you will live forever, live like you will die tomorrow.",
              author: "Mahatma Gandhi",
            },
            {
              text: "Stay away from those people who try to disparage your ambitions. Small minds will always do that, but great minds will give you a feeling that you can become great too.",
              author: "Mark Twain",
            },
            {
              text: "When you give joy to other people, you get more joy in return. You should give a good thought to happiness that you can give out.",
              author: "Eleanor Roosevelt",
            },
            {
              text: "When you change your thoughts, remember to also change your world.",
              author: "Norman Vincent Peale",
            },
            {
              text: "It is only when we take chances, when our lives improve. The initial and the most difficult risk that we need to take is to become honest.",
              author: "Walter Anderson",
            },
            {
              text: "Nature has given us all the pieces required to achieve exceptional wellness and health, but has left it to us to put these pieces together.",
              author: "Diane McLaren",
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
