<script setup lang="ts">
import { toRefs } from 'vue'
import { type Event } from '../../types'
import { useRouter } from 'vue-router'
import { useMessageStore } from '../../stores/message'

const props = defineProps<{
  event: Event
  id: String
}>()

// eslint-disable-next-line @typescript-eslint/no-unused-vars
const { event } = toRefs(props)

const router = useRouter()
const store = useMessageStore()

const saveEdit = () => {
  store.updateMessage('Event data has been updated successfully')
  setTimeout(() => {
    store.resetMessage()
  }, 3000)
  router.push({ name: 'event-detail-view', params: { id: props.event.id } })
}
</script>

<template>
  <p>Edit event here</p>
  <div class="edit-form">
    <h3>Edit Event: {{ event.title }}</h3>
    
    <div class="form-group">
      <label for="title">Event Title:</label>
      <input type="text" id="title" :value="event.title" />
    </div>
    
    <div class="form-group">
      <label for="description">Description:</label>
      <textarea id="description" rows="3" :value="event.description"></textarea>
    </div>
    
    <div class="form-group">
      <label for="location">Location:</label>
      <input type="text" id="location" :value="event.location" />
    </div>
    
    <div class="form-group">
      <label for="date">Date:</label>
      <input type="text" id="date" :value="event.date" />
    </div>
    
    <div class="form-group">
      <label for="time">Time:</label>
      <input type="text" id="time" :value="event.time" />
    </div>
    
    <div class="form-group">
      <label>
        <input type="checkbox" :checked="event.petsAllowed" /> Pets Allowed
      </label>
    </div>
    
    <button @click="saveEdit" class="save-btn">Save Changes</button>
  </div>
</template>

<style scoped>
.edit-form {
  max-width: 500px;
  margin: 20px auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: #f9f9f9;
  text-align: left;
}

.edit-form h3 {
  color: #2c3e50;
  margin-bottom: 20px;
  text-align: center;
}

.form-group {
  margin-bottom: 15px;
}

.form-group label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
  color: #2c3e50;
}

.form-group input[type="text"],
.form-group textarea {
  width: 100%;
  padding: 8px 12px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 14px;
  box-sizing: border-box;
}

.form-group input[type="checkbox"] {
  margin-right: 8px;
}

.save-btn {
  background-color: #42b983;
  color: white;
  border: none;
  padding: 12px 24px;
  border-radius: 4px;
  font-size: 16px;
  cursor: pointer;
  width: 100%;
  transition: background-color 0.3s ease;
}

.save-btn:hover {
  background-color: #369c6f;
}
</style>