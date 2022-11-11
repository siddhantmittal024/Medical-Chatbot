<template>
  <div class="grid">
    <div class="main">
      <h1>
        Medical ChatBot
        <span class="underlines">
          <span class="underline" style="margin-left: 0%"></span>
          <span class="underline" style="margin-left: 25%"></span>
          <span class="underline" style="margin-left: 50%"></span>
          <span class="underline" style="margin-left: 75%"></span>
        </span>
      </h1>

      <h2 style="margin-top: 1em">About</h2>
      <p style="margin-top: 0.5em">
        Medical ChatBot is an AI-driven chatbot that will help you answer your
        basic medical queries. The chatbot can respond to your medical queries
        only to the best of its knowledge graph base.
      </p>

      <h2 style="margin-top: 1em">Working</h2>
      <p style="margin-top: 0.5em">
        We have built a knowledge graph database of selected diseases, their
        symptoms and description. These relationships are stored in a Neo4j
        database, from where the results can be fetched.
      </p>
      <p style="margin-top: 0.5em">
        To understand user query, we make use of string matching algorithm, to
        identify the patterns of type of question asked and fetch suitable
        results.
      </p>
    </div>
    <div></div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
@import "../assets/style.css";
</style>
