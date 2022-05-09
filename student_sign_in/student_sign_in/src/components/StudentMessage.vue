<template>
  <div v-if="student.name">
    <div v-if="student.present" class="alert alert-success">
        Welcome,{{ student.name }}!
    </div>

    <div v-else class="alert alert-info" >
      Goodbye,{{ student.name }} See you later!
    </div>

  </div>
</template>

<script>
export default {
  name: 'StudentMessage',
  props:{
     student: Object
  }
}
</script>

<style scoped>

</style>