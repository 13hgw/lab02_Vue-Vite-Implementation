<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { ref } from 'vue'
import { useMessageStore } from './stores/message'
import { storeToRefs } from 'pinia'
const store = useMessageStore()
const { message } = storeToRefs(store)
const globalPerPage = ref(2)
</script>

<template>
  <div id="layout">
    <header>
      <div id="flashMessage" v-if="message">
        <h4>{{ message }}</h4>
      </div>

      <div class="wrapper">
        <nav>
          <RouterLink :to="{ name: 'event-list-view' }">Event</RouterLink> |
          <RouterLink :to="{ name: 'students' }">Students</RouterLink> |
          <RouterLink :to="{ name: 'about' }">About</RouterLink>
        </nav>
        <div class="global-page-size">
          <label>Event per page: </label>
          <select v-model="globalPerPage">
            <option value="2">Two Events</option>
            <option value="4">Four Events</option>
            <option value="6">Six Events</option>
            <option value="8">Eight Events</option>
          </select>
        </div>
      </div>
      
    </header>
    
    <RouterView :per-page="globalPerPage" />
  </div>
</template>

<style>
#layout {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
.global-page-size {
  margin: 10px 0;
  padding: 10px;
  background-color: #f8f9fa;
  border-radius: 8px;
}

.global-page-size label {
  font-weight: bold;
  margin-right: 10px;
}

.global-page-size select {
  padding: 5px 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
  background-color: white;
  cursor: pointer;
}

h2 {
  font-size: 20px;
}
@keyframes yellofade {
  from {
    background-color: yellow;
  }
  to {
    background-color: transparent;
  }
}
#flashMessage {
  animation: yellofade 3s ease-in-out;
}

</style>