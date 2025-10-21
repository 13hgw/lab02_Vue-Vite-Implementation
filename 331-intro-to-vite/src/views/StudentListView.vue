<script setup lang="ts">
import StudentCard from '../components/StudentCard.vue'
import type { Student } from '../types'
import { ref, onMounted } from 'vue'
import StudentService from '../services/StudentService'

const students = ref<Student[] | null>(null)

onMounted(() => {
  StudentService.getStudents()
    .then((response) => {
      students.value = response.data
    })
    .catch((error) => {
      console.error('There was an error fetching students!', error)
    })
})
</script>

<template>
  <div class="students">
    <h1>Student List</h1>
    <div v-if="students" class="student-list">
      <StudentCard 
        v-for="student in students" 
        :key="student.id" 
        :student="student" 
      />
    </div>
    <div v-else>
      Loading students...
    </div>
  </div>
</template>

<style scoped>
.students {
  padding: 20px;
}

.student-list {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>