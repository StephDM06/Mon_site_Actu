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

  // this.actu = [{
  //       source: { id: null, name: "Eurosport.fr" },
  //       author: "Eurosport",
  //       title:
  //         "Le tirage de la Ligue Europa (C3) en direct : Quel adversaire pour l'OL en quarts de finale ? - Eurosport FR",
  //       description:
  //         "LIGUE EUROPA - Retrouvez le tirage au sort des quarts de finale de la Ligue Europa sur Eurosport, où l'OL sera le seul représentant français.",
  //       url: "https://www.eurosport.fr/football/ligue-europa/2021-2022/le-tirage-de-la-ligue-europa-en-direct-quel-adversaire-pour-l-ol-en-quarts-de-finale_sto8849309/story.shtml",
  //       urlToImage:
  //         "https://i.eurosport.com/2022/03/18/3339760-68275468-2560-1440.jpg",
  //       publishedAt: "2022-03-18T12:30:00Z",
  //       content:
  //         "Lucas Paqueta lors de Lyon-Porto en Ligue Europa.\r\nCrédit: Getty Images",
  //     },
  //     {
  //       source: { id: null, name: "jeuxvideo.com" },
  //       author: "Damien-Scaletta",
  //       title:
  //         "Hogwarts Legacy : Avalanche a une excellente nouvelle pour les joueurs ! - jeuxvideo.com",
  //       description:
  //         "Hogwarts Legacy : L'Héritage de Poudlard a soulevé des questions de fans lors de sa présentation au State of Play : y'aura-t-il des microtransactions ? Lors de la présentation de Hogwarts Legacy au State of Play, un élément a surpris les joueurs : certaines m…",
  //       url: "https://www.jeuxvideo.com/news/1547403/hogwarts-legacy-avalanche-a-une-excellente-nouvelle-pour-les-joueurs.htm",
  //       urlToImage:
  //         "https://image.jeuxvideo.com/medias-md/164760/1647601523-1814-card.png",
  //       publishedAt: "2022-03-18T11:10:08Z",
  //       content:
  //         "Hogwarts Legacy : L'Héritage de Poudlard a soulevé des questions de fans lors de sa présentation au State of Play : y'aura-t-il des microtransactions ?\r\nLors de la présentation de Hogwarts Legacy au … [+1705 chars]",
  // }];
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
}
</style>