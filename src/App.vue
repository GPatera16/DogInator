<template>

 <dog-generate></dog-generate>
</template>


<script>
import "./main.js";
import "./components/DogGenerate.vue";
import DogGenerate from './components/DogGenerate.vue';


export default {
  name:'app',
  data(){
    return{
      url_base:"https://dog.ceo/api/breeds/image/random",
      dog: {},
      image:"",
      name_url:"https://random-word-api.herokuapp.com/word?lang=it",
      name:"",
    }
  },
  methods:{
    fetchShop(){
      fetch(this.url_base)
      .then(res=>{
        return res.json();
      }).then(this.setResults);
    },
    fetchName(){
      fetch(this.name_url)
      .then(res=>{
        return res.json();
      }).then(this.setName);
    },
    setResults(results){
      this.dog=results;
      this.image=this.dog.message;
    },
    setName(name){
      this.name=name;
    },
    
  },
  components: {
    DogGenerate
  }
  
}
</script>

<style>

</style>