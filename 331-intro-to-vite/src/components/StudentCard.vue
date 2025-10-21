<script setup lang="ts">
import type { Student } from '../types'

defineProps<{
  student: Student
}>()
</script>

<template>
  <div class="student-card">
    <h2>{{ student.name }} {{ student.surname }}</h2>
    <div class="student-info">
      <span class="gpa">GPA: {{ student.gpa }}</span>
    </div>
  </div>
</template>

<style scoped>
.student-card {
  padding: 20px;
  width: 250px;
  border: 1px solid #39495c;
  margin-bottom: 18px;
  border-radius: 8px;
  background-color: #f9f9f9;
}

.student-card:hover {
  transform: scale(1.01);
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2);
}

.student-info {
  margin-top: 10px;
}

.gpa {
  font-weight: bold;
  color: #2c3e50;
}
</style>