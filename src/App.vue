<template>
  <v-app>

    <v-app-bar
      app
    >
      <v-spacer></v-spacer>
      <span class="h3">
        Total: {{total}}
      </span>
      <v-spacer></v-spacer>
    </v-app-bar>

    <v-main>
      <v-container fluid>
        <v-checkbox v-model="highlightPrimes" label="Primes"></v-checkbox>
        <v-row v-for="num in numGrid" :key="num.id">
          <v-col v-for="col in num" :key="col.id">
            <div v-if="col.isPrime" :class="highlightPrimes ? 'is-prime' : 'rectangle'">
              {{ col.num }}
            </div>
            <div v-else class="rectangle">
              {{ col.num }}
            </div>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'App',

  components: {
  },
  
  data() {
    return {
      numGrid: [],
      numArray: [],
      highlightPrimes: false,
    }
  },
  computed: {
    total() {
      let total = 0
      if (this.highlightPrimes) {
        this.numArray.forEach(element => {
          if(element.isPrime) {
            total += element.num
          }
        });
        return total
      } else {
        this.numArray.forEach(element => {
          total += element.num
        })
        return total
      }
    }
  },
  methods: {
    isPrime() {
      let count = 1
      for (let row = 0; row < 10; row++) {
        this.numGrid[row] = []
        console.log(this.numGrid)
        for (let col = 0; col < 10; col++) {
          if(count === 2 || count === 3 || count === 5 || count === 7){
            this.numGrid[row].push({
              isPrime: true,
              num: count
            })
            this.numArray.push({
              isPrime: true,
              num: count
            })
          }
          else if(count % 2 === 0 || count % 3 === 0 || count % 5 === 0 || count % 7 === 0 || count === 1) {
            this.numGrid[row].push({
              isPrime: false,
              num: count
            })
            this.numArray.push({
              isPrime: false,
              num: count
            })
          } else {
            this.numGrid[row].push({
              isPrime: true,
              num: count
            })
            this.numArray.push({
              isPrime: true,
              num: count
            })
          }
          count++
        }
      }
      console.log(this.numGrid)
    }
  },
  created() {
    this.isPrime()
  }
};
</script>

<style scoped>
.rectangle {
  background: rgb(190, 190, 190);
  text-align: center;
  line-height: 5vh;
  width: 5vw;
  height: 5vh;
}
.is-prime {
  background: rgb(250, 243, 142) !important;
  text-align: center;
  line-height: 5vh;
  width: 5vw;
  height: 5vh;
}
</style>
