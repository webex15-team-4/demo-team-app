<template>
  <!DOCTYPE html>
  <html lang="ja">
    <head>
      <meta charset="UTF-8" />
      <meta name="viewport" content="width=device-width, initial-scale=1.0" />
      <meta http-equiv="X-UA-Compatible" content="ie=edge" />
      <title>Document</title>
    </head>
    <body>
      <div id="app">
        <h2>Q. {{ quiz.text }}</h2>
        <img
          id="quiz-image"
          v-bind:src="quizImagePath"
          v-bind:alt="quiz.text"
        />
        <div class="container">
          <button
            v-for="(choice, i) in quiz.choices"
            v-bind:key="i"
            v-on:click="choiced(choice)"
          >
            {{ choice.text }}
          </button>
        </div>
        <div>{{ feedback }}</div>
      </div>
    </body>
  </html>
</template>

<script>
export default {
  data() {
    return {
      feedback: "",
      quiz: {
        text: "この星の名前は何でしょう？",
        image: "./assets/assets/Ganymede.jpg",
        choices: [
          {
            text: "ゴリアテ",
            isCorrect: false,
            feedback:
              "残念！ゴリアテは、旧約聖書に登場するダビデに石で殺される巨人だよ。",
          },
          {
            text: "ゼニガメ",
            isCorrect: false,
            feedback:
              "残念！ゼニガメは、クサガメまたはニホンイシガメの幼体だよ。",
          },
          {
            text: "ガニメデ",
            isCorrect: true,
            feedback: "正解！ガニメデは、木星の第三惑星だよ！",
          },
        ],
      },
    }
  },
  methods: {
    choiced(choice) {
      this.feedback = choice.feedback

      if (choice.isCorrect) {
        // 次の問題へ
      }
    },
  },
  computed: {
    quizImagePath() {
      return this.quiz.image
    },
  },
}
</script>

<style>
#app {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}
#quiz-image {
  height: 300px;
  width: 300px;
  object-fit: contain;
}
.container {
  display: flex;
  height: 2em;
  width: 300px;
  padding: 1em;
  justify-content: space-around;
}
</style>
