<template>
  <div id="app">
      <div class="quote"><h1>{{ quote }}</h1></div>
      
      <button @click='getRon'>Give Me Another</button>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'app',
  data () {
    return {
      quote: ''
    }
  },
  methods:{
    getRon(){
      axios.get(`http://ron-swanson-quotes.herokuapp.com/v2/quotes`)
      .then(response => {
      // JSON responses are automatically parsed.
      this.quote = response.data[0];
      })
     .catch(e => {
      this.errors.push(e)
      });

      }
  },

  mounted() {

    axios.get(`http://ron-swanson-quotes.herokuapp.com/v2/quotes`)
    .then(response => {
      // JSON responses are automatically parsed.
      this.quote = response.data[0];
    })
    .catch(e => {
      this.errors.push(e)
      });
    }
    
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #fff;
  display: flex;
  align-items: center;
  flex-direction: column;
  
 
  
  width: 50%;
}

.quote{
   display: flex;
   justify-content: center;
   align-items: center;
   background-image: url('/src/assets/ron-swanson.jpg');
   background-repeat: no-repeat;
   height: 400px;
   width: 100%;
   height: 500px;

}

h1, h2, button{
  font-weight: normal;
  font-size: 2em;
  margin: 1em;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
