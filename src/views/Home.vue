<template>
  <div class="home">
    <h1>Common Quotes</h1><hr><br>
    <div class="container"  v-for="quote in quotes" :key="quote.id">
        
        <p>{{ quote.text }}</p>
        <h2>{{ quote.author }}</h2>
        
    </div>
    
    <footer>
      <p>Copyright &copy; 2021 </p>
    </footer>
  </div>
</template>

<script>
import axios from 'axios';

export default {
 
  data(){
    return{
      quotes: []

    }
    
  },

  created(){
    axios.get('https://type.fit/api/quotes')
    .then(res => this.quotes = res.data)
    .catch(err => console.log(err));
    }

  }

</script>

<style>
.container{
  background: #dd3;
}

footer{
  position: relative;
}

footer p{
  position: absolute;
   bottom: -2%;
   background: #333;
   width: 100%;
   color: #fff;
   padding: 10px;
}

</style>

