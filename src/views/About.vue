<template>
  <article class="about container">
    <h1>This is an about page</h1>

     <Boot />



  </article>
</template>

<script>
// @ is an alias to /src
import Boot from '@/components/Boot.vue'

export default {
  name: "About",

  components: {
    Boot
  }

}
</script>
