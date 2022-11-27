<template>
  <div class="home">
    <div class="id">
     <div v-if="id">ADVICE  #{{ id }}</div>
      <br>
      <br>
    </div>
    <div class="advice">
      <div v-if="advice">" {{ advice }} ,,</div>
    </div>

  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'Home',
  data() {
    return {
      advice: "",
      id:""
    }
  },
  mounted () {
    this.getAdvice()
  },
  methods: {
    async getAdvice() {
      const res = await axios.get(`https://api.adviceslip.com/advice`);
      this.advice = res.data.slip.advice
      this.id = res.data.slip.id
    },

  }
}
</script>

<style >
  .home{
    background: #2c3e50;
    color: aliceblue;
    margin:  20%;
    border-radius: .5em;
    padding-bottom: 2em;
    font-weight: 700;
  }

.id{
  color: #42b983;
  padding-top: 2em;
  font-size: .8em;
  letter-spacing: 2px;
}

.advice{
  font-size: 1.4em;
  font-weight: 800;

}
</style>
