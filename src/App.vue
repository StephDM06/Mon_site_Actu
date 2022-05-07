<template>
<div>
  
  <nav id="navbar">
    <h1>Les actus de Lulu</h1>
    <h2>La fraicheur des news, sous la blouse</h2>
    <div id="bouton">
      <label for="research">Votre recherche :</label>
      <input type="text" name="research" id="research" v-model.lazy="recherche"/>
    </div>
  </nav>
      <Arti v-for="(element,index) in actu" :key="index"
          :auteur="element.author"
          :titre="element.title"
          :date="element.publishedAt"
          :description="element.description"
          :urlimage="element.urlToImage"        
          :lien="element.url"
      >
      </Arti>
 
</div>
</template>

<script>
import Arti from "./components/article.vue";


const Debut={
  data(){
    return{
      actu:[],
      recherche:"",
      theme:"",
    };
  },
components:{
 Arti: Arti,
},

 async mounted(){
   const retour= await fetch("https://newsapi.org/v2/top-headlines?country=fr&apiKey=562d7784a1214bb09c14d88880972cd9");

  let data= await retour.json();
 this.actu= data.articles;
 
 },


};
export default Debut;
</script>

<style scoped>
#navbar{
 text-align: center;
}
#bouton{
  display: flex;
  justify-content: right;
  width: 300px;
  padding-right: 0px;
  margin-bottom: 15px;
}
</style>