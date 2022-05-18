<template>
  <section class="advice__container" v-for="item in list" :key="item.id">
      <h5 class="advice__title">ADVICE #{{item.id}}</h5>
      <p class="advice__para">{{item.advice}}</p>
      <img src="../assets/pattern-divider-mobile.svg" alt="divider" class="advice__mobile">
      <img src="../assets/pattern-divider-desktop.svg" alt="divider" class="advice__desktop">
      <div class="advice__btn" @click="RandomAdvice">
          <img src="../assets/icon-dice.svg" alt="button">
      </div>
  </section>
</template>

<script>


export default {
    data () {
        return {
            list: [],
            number: 1   
        }
    },
    methods: {
        async RandomAdvice() {
            this.number++
            await this.getAdvice()
        },
        async getAdvice() {
            const fetchData = await fetch(`https://api.adviceslip.com/advice/${this.number}`)
            this.list = await fetchData.json()  
        },
    },
    created() {
       this.getAdvice()
    }
     
}
</script>

<style>
.advice__container {
    height: 315px;
    width: 335px;
    background: hsl(217, 19%, 24%);
    text-align: center;
    color: hsl(193, 38%, 86%);
    margin: auto;
    border-radius: 10px;
}

.advice__title {
    font-size: 10px;
    letter-spacing: 5px;
    margin: 40px auto 25px;
    color: hsl(150, 100%, 66%);
}

.advice__para {
    text-align: center;
    font-size: 22px;
    height: 120px;
    padding: 0px 15px;
    
}

.advice__btn {
    height: 65px;
    width: 65px;
    border-radius: 50%;
    background: hsl(150, 100%, 66%);
    margin: 30px auto;
    cursor: pointer; 
}

.advice__btn:hover {
    box-shadow: 0 0 50px hsl(150, 100%, 66%);
}
.advice__btn > img {
    margin: 20px;
}

.advice__desktop {
    display: none;
}

@media only screen and (min-width: 999px) {
    .advice__container {
        width: 540px;
        height: 330px;
        padding: 0px 45px;
    }

    .advice__para {
        margin-bottom: 30px;
    }
    .advice__btn {
        margin-top: 50px;
    }
    .advice__desktop {
        display: block;
    }

    .advice__mobile {
        display: none;
    }
  }
</style>