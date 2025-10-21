<script setup lang="ts">
import type { Event } from '../types'

defineProps<{
  event: Event
}>()
</script>

<template>
  <div class="event-meta">
    <div class="category">{{ event.category }}</div>
    <div class="organizer">{{ event.organizer }}</div>
  </div>
</template>

<style scoped>
.event-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 14px; /* 相同的字体大小 */
  text-align: right; /* 文本右对齐 */
  width: 100%;
  margin-top: 10px;
}

.category, .organizer {
  font-size: 14px; /* 确保两者字体大小相同 */
}
</style>