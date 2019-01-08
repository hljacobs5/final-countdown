<template>
  <div class="picture-container">
    <h2>Date</h2>
      <button v-on:click='getResult()'>Today's Picture</button>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'app',
  data () {
    return {
      msg: 'Pictures',
      date: '',
      result: ''
    }
  }, 
  methods: {
    getResult() {
      // const todaysDate = '2019-07-01'
      axios.get('https://images-api.nasa.gov/search?media_type=image&q=sun&page=2')
        .then(response => { console.log(response.data.collection.links.map(key => {
          key.href
        }));
        this.result = response.data.collection.links.map(key => {
          key.href
        });
      });
    }
  }
}
</script>


<style scoped>
.picture-container {
  background: black;
}

h1, h2 {
  font-weight: normal;
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
