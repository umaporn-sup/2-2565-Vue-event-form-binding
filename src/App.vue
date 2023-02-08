<script setup>
import { ref } from 'vue'
const darkTheme = ref(false)
const yourColor = ref('#eca7dd')
const studentId = ref('')
const entryYear = ref('')
const findEntryYear = (e, digits) => {
  entryYear.value = studentId.value.substring(0, digits)
  console.log(e.target.id)
  console.log(e.target.name)
  console.log(e.target.tagName)
}
const dyImage = 'images/astronaut.jpg'
</script>
<template>
  <div class="w-full h-screen flex flex-col favoriteBg">
    <div>
      <div class="w-full flex space-x-2">
        <h3>Your Favorite Color:</h3>
        <input type="color" v-model="yourColor" /> {{ yourColor }}
      </div>
      <div class="w-full flex flex-row space-x-2 justify-end p-2">
        <h3>Dark Mode</h3>
        <input type="checkbox" class="toggle" checked v-model="darkTheme" />
        {{ darkTheme }}
      </div>
    </div>
    <div class="w-full flex-col">
      <div class="flex space-x-2">
        <label for="">Student Id:</label>
        <input
          type="text"
          placeholder="64XXXXXXXXX"
          class="border border-gray-300 p-1"
          v-model="studentId"
          @keyup.enter="findEntryYear($event, 3)"
        />
        <!-- <button                    @click="findEntryYear($event, 3)"                    class="rounded-xl bg-emerald-600 text-white p-1"                    id="btn-001"                    name="findEntryYearbtn"                >                    OK                </button> -->
      </div>
      <div class="flex space-x-2">
        <p>
          Entry Year: <span>{{ entryYear }}</span>
        </p>
      </div>
    </div>
    <div class="w-full flex-col">
      <div class="flex">
        <h3>Static Image:</h3>
        <img src="./assets/logo.svg" class="w-32 h-32" />
      </div>
      <div class="flex">
        <h3>Dynamic Images:</h3>
        <img :src="dyImage" class="w-32 h-32" />
      </div>
    </div>
  </div>
</template>
<style scoped>
.favoriteBg {
  background-color: v-bind(yourColor);
}
</style>
