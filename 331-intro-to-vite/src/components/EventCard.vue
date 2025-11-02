<script setup lang="ts">
import { type Event } from '../types'
import EventMeta from './EventMeta.vue'

defineProps<{
  event: Event
}>()
</script>

<template>
  <RouterLink 
    class="block no-underline text-gray-800 transition-all duration-300 hover:no-underline" 
    :to="{ name: 'event-detail-view', params: { id: event.id } }"
  >
    <div class="cursor-pointer border border-gray-300 p-5 w-64 mb-4 bg-white rounded-lg shadow-sm 
                hover:scale-105 hover:shadow-lg hover:border-blue-300 hover:bg-blue-50 
                transform transition-all duration-300 ease-in-out">
      <h2 class="text-xl font-semibold mb-2 text-gray-800 line-clamp-2 
                 group-hover:text-blue-700 transition-colors duration-300">
        {{ event.title }}
      </h2>
      <span class="text-gray-600 text-sm block mb-3 
                   group-hover:text-blue-600 transition-colors duration-300">
        @{{ event.time }} on {{ event.date }}
      </span>
      <EventMeta :event="event" />
    </div>
  </RouterLink>
</template>

<style scoped>
/* .event-card {
  padding: 20px;
  width: 250px;
  cursor: pointer;
  border: 1px solid #39495c;
  margin-bottom: 18px;
} */

/* .event-card:hover {
  transform: scale(1.01);
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2);
} */

.event-link {
  text-decoration: none;
  color: #2c3e50;
}
</style>