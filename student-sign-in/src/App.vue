<template>
  <div id="app">
   
    <new-student-form v-on:Student-added="newStudentAdded"></new-student-form>
    <student-table v-bind:students="students" v-on:student-arrived-or-left="studentArriveOrLeft" v-on:delete-student="studentDeleted"></student-table>
    <student-message v-bind:student="mostRecentStudent"></student-message>

  </div>
</template>

<script>
import NewStudentForm from './components/NewStudentForm.vue'
import StudentMessage from './components/StudentMessage.vue'
import StudentTable from './components/StudentTable.vue'

export default {
  name: 'App',
  components: {
    NewStudentForm ,
    StudentMessage,
    StudentTable
  },
  data () {
    return {
      students: [] ,
      mostRecentStudent: {

      }
    }
  },
  methods: {
    newStudentAdded(student) {
      this.student.push(student)
      this.students.sort(function(s1, s2) {
        return s1.name.toLowerCase() < s2.name.toLowerCase() ? -1 : 1
      })
    },
    studentArriveOrLeft(student, present) {
      // find student in array of students
      // update present attribute

      let updateStudent = this.students.find( function(s) {
        if (s.name === student.name && s.startID === student.startID) {
          return true
        }
      })

      if (updateStudent) {
        updateStudent.present = present
        this.mostRecentStudent = updateStudent
      }
    },
    studentDeleted(student) {
      this.students = this.students.filter( function(s) {
        if (s != student) {
          return true
        }
      })

      this.mostRecentStudent = {}
    }
  }
}
</script>

<style>

@import "https://cdn.jsdelivr.net/npm/bootstrap@4.0.0/dist/css/bootstrap.min.css"


</style>
