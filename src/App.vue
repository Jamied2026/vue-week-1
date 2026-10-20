<script setup>
import { ref, computed } from 'vue'
const newExercise = ref('')
const newMinutes = ref(15)
const errorMessage = ref('')
let nextId = 3
const exercises = ref([
  { id: 1, name: 'Walking', minutes: 20, completed: false },
  { id: 2, name: 'Stretching', minutes: 10, completed: false }
])
</script>


<template>
  <main class="dashboard">
    <header class="hero">
      <p class="eyebrow">YOUR DAILY WORKOUT PLANNER</p>
      <h1>Shape Up</h1>
      <p>Small steps. Stronger habits.</p>
    </header>
    <!-- STEP 7: Progress summary goes here. -->
    <div class="dashboard-grid">
      <section class="panel">
        <h2>Plan an exercise</h2>
        <!--step 5 -->
        <form @submit.prevent="addExercise">
          <label for="exercise-name">Exercise name</label>
          <input id="exercise-name" v-model="newExercise" type="text"
                 placeholder="For example, cycling"maxlength="60"required>
          <label for="exercise-minutes">Duration in minutes</label>
          <input id="exercise-minutes"v-model.number="newMinutes"
                 type="number"min="1" max="180" step="1" required>

          <button type="submit" class="primary-button">Add exercise</button>
          <p v-if="errorMessgae" class="error-message" role="alert">
            {{errorMessage}}
          </p>
        </form>
      </section>
      <section class="panel">
        <h2>Your workout</h2>
        <p v-if="exercises.length===0" class="empty-state">
        </p>
        <ul v-else class="exercise-list">
          <li v-for="exercise in exercises" :key="exercise.id"
              class="exercise"
              :class="{completed:exercise.completed}">
            <label class="exercise-details">
              <input type="checkbox" v-model="exercise.completed">
              <span>
                <strong>{{exercise.name}}</strong>
                <small>{{exercise.minutes}}minutes</small>
              </span>
            </label>
            <!-- STEP 6: Remove button goes here. -->
          </li>
        </ul>
      </section>
    </div>
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
