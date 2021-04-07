<template>
  <div>
    <h2>"{{ preamble }}"</h2>
    <button @click="countWords">Count Words</button>
    <div>
      <h4>Words that begin with "T": {{ startsWithT }}</h4>
      <h4>Words that end with "E": {{ endWithE }}</h4>
      <h4>Words that begin with "T" and end with "E": {{ both }}</h4>
    </div>
  </div>
</template>

<script>
import data from "./data";

export default {
  data() {
    return {
      preamble: data.text,
      startsWithT: 0,
      endWithE: 0,
      both: 0
    };
  },
  methods: {
    countWords() {
      const wordsOnly = this.preamble
        .replace(/[^a-zA-Z ]/g, "", "")
        .toLowerCase();

      const wordArray = wordsOnly.split(" ");

      const tWords = [];
      const eWords = [];
      const tandeWords = [];

      for (let i = 0; i < wordArray.length; i++) {
        if (wordArray[i].startsWith("t")) {
          tWords.push(wordArray[i]);
        }
        if (wordArray[i].endsWith("e")) {
          eWords.push(wordArray[i]);
        }
        if (wordArray[i].startsWith("t") && wordArray[i].endsWith("e")) {
          tandeWords.push(wordArray[i]);
        }
      }

      this.startsWithT = tWords.length;
      this.endWithE = eWords.length;
      this.both = tandeWords.length;
    }
  }
};
</script>

<style>
</style>