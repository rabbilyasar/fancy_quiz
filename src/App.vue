<template>
  <div id="app">
    <Header 
      :numCorrect="numCorrect"
      :numTotal="numTotal"
    />
    <b-container class="bv-example-row">
      <b-row>
      <b-col>
        <QuestionBar 
          v-if="questions.length"
          :currentQuestion="questions[index]"
          :next="next"
          :increment="increment"
        />
      </b-col>
      </b-row>
      <!-- {{questions}} -->
    </b-container>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import QuestionBar from "./components/QuestionBar";
import axios from 'axios'

export default {
  name: "app",
  components: {
    Header,
    QuestionBar
  },

  data () {
    return {
      questions: [],
      index: 0,
      numCorrect: 0,
      numTotal: 0
    }
  },

  methods: {
    next() {
      this.index++
    },
    increment(isCorrect) {
      if (isCorrect) {
        this.numCorrect++
      }
      this.numTotal++
    }
  },

  mounted() {
    axios.get('https://opentdb.com/api.php?amount=10&type=multiple')
      .then(res => {
        // console.log(res)
        this.questions = res.data.results
      })
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
</style>
