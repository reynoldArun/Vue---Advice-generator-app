<template>
  <main>
    <Advice />
  </main>
</template>

<script>

import Advice from './components/Advice.vue'

export default {
    components: { Advice }
} 

</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Manrope:wght@800&display=swap');


  *, *::before, *::after {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }

  body {
    font-size: 28px;
    font-family: 'Manrope', sans-serif;
    background: hsl(218, 23%, 16%);
    height: 100vh;
  }
  main {
    display: flex;
    height: 50vh;
  }

  @media only screen and (min-width: 999px) {
    main {
      height: 100vh;
    }
  }

</style>