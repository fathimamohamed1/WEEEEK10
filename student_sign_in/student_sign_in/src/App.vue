<template>
 <new-student-form v-on:student-added="newstudentadded"></new-student-form>

  <student-message v-bind:student="mostRecentStudent"></student-message>

  <student-table v-bind:students="students"
                 v-on:student-arrived-or-left="studentArrivedOrLeft"
                 v-on:delete-student="deleteStudent">

  </student-table>

</template>

<script>
import NewStudentForm from './components/NewStudentForm.vue'
import StudentMessage from './components/StudentMessage'
import StudentTable from './components/StudentTable.vue'
export default {
  name: 'App',
  components: {
    NewStudentForm,
    StudentMessage,
    StudentTable
  },
  data(){
    return{
      students:[],
      mostRecentStudent:{}
    }
  },
  methods:{
    newstudentadded(student){
      this.students.push(student)
      this.students.sort(function (s1,s2){
      return s1.name.toLowerCase() < s2.name.toLowerCase()?-1:1
      })
    },
    studentArrivedOrLeft(student,present){
      let updateStudent=this.students.find(function (s){
        if(s.name===student.name&& s.starID===student.starID){
          return true
        }
      })
      if(updateStudent){
        updateStudent.present=present
        this.mostRecentStudent=student
      }
    },
    deleteStudent(student) {
      this.students=this.students.filter(function (s){
        if(s != student){
          return true
        }
      })
    }
  }
}
</script>

<style>

@import "https://cdn.jsdelivr.net/npm/bootstrap@4.6.1/dist/css/bootstrap.min.css";

</style>
