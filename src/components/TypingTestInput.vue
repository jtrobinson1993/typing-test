<template>
  <div class="typing-input">
    <div class="typing-input__prev"></div>
    <input
      class="typing-input__entry"
      type="text"
      v-on:keyup="checkInputCorrect"
      v-on:keydown="checkKeyCode"
      v-model="userInput"
    >
    <div class="typing-input__next">
      <span
        class="typing-input__upcoming-word"
        v-for="(text, index) in upcomingText"
        :key="index"
      >{{text}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "TypingTestInput",
  data: () => {
    return {
      completedText: ["Lorem", "ipsum", "dolor", "sit", "amet"],
      upcomingText: ["Lorem", "ipsum", "dolor", "sit", "amet"],
      userInput: ""
    };
  },
  methods: {
    checkInputCorrect: function() {
      //   let currentLetter = 0;
      //   const typedLetter = this.e;

      const nextLetter = this.upcomingText[0].split("")[0];
      if (this.userInput === nextLetter)
        this.upcomingText[0] = this.upcomingText[0].slice(1);
      if (this.upcomingText[0] === "") this.upcomingText.shift();
      this.userInput = "";
    },
    checkKeyCode: function(e) {
      console.log(e.key);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
</style>
