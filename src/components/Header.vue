<template>
  <div class="header">
    <h1> {{ name }}</h1>
  </div>
</template>

<script>
  export default {
    name: "header",
    props: {
      name: String,
    },
  }
</script>

<style scoped>
 .header {
   background-color: purple;
   margin: 0;
 }
 h1 {
   color:antiquewhite;
   margin: 0;
   font-size: 5rem;
 }

</style>