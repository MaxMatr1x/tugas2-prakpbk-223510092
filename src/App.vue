<template>
  <div :style="{ backgroundColor: containerBackground }" class="container">
    <h1 :style="{ color: titleColor }">LIFE STORIES</h1>
    <div class="quote">
      <p class="quote-text">"Dunia bukan hanya untuk orang yang kuat <br>tetapi juga untuk orang yang mampu bertahan"</p>
      <p class="quote-author">- Matrix (07 Mei 2024)</p>
    </div>
    <div class="note">
      <p class="note-label">Cerita Hari Ini:</p>
      <textarea v-model="dailyNote" :style="{ background: placeholderColor }" placeholder="Tulis cerita hari ini"></textarea>
    </div>
    <div class="color-buttons">
      <button :class="{ 'white-button': placeholderColor === 'white' }" @click="changePlaceholderColor('white')">Latar 1</button>
      <button :class="{ 'green-button': placeholderColor === 'lightgreen' }" @click="changePlaceholderColor('lightgreen')">Latar 2</button>
      <button :class="{ 'cyan-button': placeholderColor === 'cyan' }" @click="changePlaceholderColor('cyan')">Latar 3</button>
      <button :class="{ 'blue-button': placeholderColor === 'lightblue' }" @click="changePlaceholderColor('lightblue')">Latar 4</button>
    </div>
    <br>
    <button class="save-button" @click="saveNote">Simpan Cerita</button>
    <br>
    <div v-if="savedNote" class="saved-note-placeholder">
      <p>Cerita yang disimpan :</p>
      <textarea v-model="savedNote" :style="{ background: placeholderColor, color: textColor }" placeholder="Catatan yang tersimpan"></textarea>
    </div>

  </div>
</template>

<script setup>
import { ref } from 'vue'

const dailyNote = ref('')
const placeholderColor = ref('white') 
const containerBackground = ref('grey') 
const titleColor = ref('#2F4F4F') 
const savedNote = ref(localStorage.getItem('dailyNote'))


function saveNote() {
  localStorage.setItem('dailyNote', dailyNote.value);
  savedNote.value = dailyNote.value; 
}

function changePlaceholderColor(color) {
  placeholderColor.value = color
}
</script>

<style scoped>

.container {
  max-width: 600px;
  margin: 50px auto;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  background-color: rgba(130, 4, 4, 0.8);
}

h1 {
  text-align: center;
}

.quote {
  margin-bottom: 20px;
  padding: 10px;
  background-color: rgb(255, 250, 250);
  border-radius: 5px;
}

.quote-text {
  font-style: italic;
}

.quote-author {
  text-align: right;
}

.note {
  margin-bottom: 20px;
}

.note-label {
  font-weight: bold;
}

textarea {
  width: 100%;
  height: 100px;
  border: 1px solid #ccc;
  border-radius: 5px;
  padding: 1px;
  font-size: 16px;
  resize: none;
}

.save-button {
  display: block;
  width: 100%;
  padding: 10px;
  border: none;
  border-radius: 5px;
  background-color: rgb(21, 123, 67);
  color: white;
  font-size: 16px;
  cursor: pointer;
}

.color-buttons {
  margin-top: 10px;
  display: flex;
  justify-content: center;
}

.color-buttons button {
  margin: 0 10px;
  padding:5px 10px;
  border:none;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;
}

.cyan-button {
  background-color: cyan;
  color: white;
}

.blue-button {
  background-color: blue;
  color: white;
}

.green-button {
  background-color: green;
  color: white;
}

.white-button {
  background-color: 	rgb(69, 60, 60);
  color: white;
}
</style>
