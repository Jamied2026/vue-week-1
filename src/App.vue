<script setup>
import { ref } from 'vue'

const name = ref('Joe Bloggs')
const bio = ref('I am learning to build interactive web pages.')
// TASK 4: Create a reactive likes counter.
const likes = ref(0);
// TASK 5: Create reactive showFact and fact values.
const showFact = ref(false);
const fact = ref('I can name five constellations.')
</script>

<template>
  <main>
    <article class="card">
      <p class="eyebrow">MY FIRST VUE PAGE</p>
      <h1>{{ name }}</h1>
      <p>{{ bio }}</p>
      <!-- TASK 2: Add a labelled input with v-model="name" here. -->
      <label for="name">Your Name:</label>
      <input id="name" v-model="name"maxlength="60">
      <!--bio-->
      <label for ="bio">Your Bio:</label>
      <input id="bio" v-model="bio"maxlength="60">
      <!-- TASK 4: Add a button, click counter and @click here. -->
    <button type="button"@click="likes++">Like this page</button>
      <button type="button"@click="likes=0">Reset Likes</button>
      <p aria-live="polite">Likes: {{likes}}</p>
      <!-- TASK 5: Add a toggle button and v-if paragraph here. -->
      <button type="button" @click="showFact=!showFact"
              :aria-expanded="showFact"aria-controls="fact">
        {{ showFact ? 'Hide fun fact' : 'Show fun fact'}}
      </button>
      <p id="fact" v-if="showFact">{{fact}}</p>
    </article>
  </main>
</template>

<style>
* { box-sizing: border-box; }
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #B3FCFB; /*change 1*/
  color: #437877;      /*change 2*/
}
main {min-height: 100vh; display: grid; place-items: center; padding: 24px; }
.eyebrow { color: #24634a; font-size: 12px; font-weight: bold; letter-spacing: 2px; }
h1 { overflow-wrap: anywhere; }
label { display: block; margin-top: 24px; font-weight: bold; }
input { width: 100%; padding: 12px; margin-top: 8px; border: 1px solid #637580; border-radius: 8px; font: inherit; }
:focus-visible { outline: 3px solid #b55000; outline-offset: 3px; }
/* TASK 3: Personalise the background, card, heading and buttons. */
button { padding: 12px 16px; margin: 16px 8px 0 0; border: 0; border-radius: 8px; background: #ABD1D0; color: white; font: inherit; cursor: pointer;}/*change 3*/
button:hover { background: #4B6969; }/*change4*/
.card { width: 100%; max-width: 520px; padding: 36px; background: white; border-radius: 18px; } /*padding changed to 36*/
</style>
