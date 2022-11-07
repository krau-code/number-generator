<template>
  <div id="container">
    <Header />

    <Form :lottoGames="lottoGames" @generate="generate" />

    <!-- Random Numbers -->
    <div class="flex" v-if="randomNumbers.length > 0">
      <div v-for="number in randomNumbers" :key="number">
        <input class="box" type="text" :value="number" disabled>
      </div>
    </div>

    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';
import Form from './components/Form.vue';

export default {
  name: 'App',
  components: { 
    Header,
    Footer,
    Form
  },
  data() {
    return {
      randomNumbers: [],
      lottoGames: [
        {
          id: 1,
          name: "Lotto 6/42",
          digit: 6,
          lastNumber: 42
        },
        {
          id: 2,
          name: "Mega Lotto 6/45",
          digit: 6,
          lastNumber: 45
        },
        {
          id: 3,
          name: "Super Lotto 6/49",
          digit: 6,
          lastNumber: 49
        },
        {
          id: 4,
          name: "Grand Lotto 6/55",
          digit: 6,
          lastNumber: 55
        },
        {
          id: 5,
          name: " Ultra Lotto 6/58",
          digit: 6,
          lastNumber: 58
        }
      ]
    }
  },
  methods: {
    generate(chosenGame) {
      const filtered = this.lottoGames.find(lottoGame => lottoGame.id == chosenGame);

      if (this.randomNumbers) {
        // while (this.randomNumbers.length > 0) {
        //   this.randomNumbers.pop();
        // }
        this.randomNumbers = [];
      }

      while (this.randomNumbers.length < filtered.digit) {
        const rand = Math.floor((Math.random() * filtered.lastNumber) + 1);
        
        if (this.randomNumbers.indexOf(rand) === -1) {
          this.randomNumbers.push(rand);
        }
      }
    }
  }
}
</script>

<style>
  #container {
    margin: 0 10rem;
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  } 

  .flex {
    max-width: 500px;
    margin: 60px auto;
    padding: 0 10px;
    display: flex;
    justify-content: space-around;
    gap: 10px;
  }

  .box {
    width: 70px;
    height: 70px;
    border-radius: 10px;
    border: 0;
    background: #393E46;
    color: #eee;
    text-align: center;
    font-family: 'Poppins', sans-serif;
    font-size: 1.5em;
  }

  @media (max-width: 481px) {
    #container {
      margin: 0 0.7em;
    }

    .flex {
      flex-wrap: wrap;
      justify-content: center;
    }
  }
</style>