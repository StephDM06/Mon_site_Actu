<template>
    <div>
        <section id="container">
        <article id="objet">
            <h1>{{titre}}</h1>
            <p>le {{date}}</p>
            <p>par :{{auteur}}</p>
            <p>{{description}}</p>
            <a :href="lien">C'est par ici pour la suite</a>
            <img class="articlePhoto" :src="urlimage"/>
        </article>
        </section>
        
    </div>
</template>

<script>
const Arti={

  props:{
    auteur:String,
    titre:String,
    description:String,
    urlimage:String,
    date:String,
   
    lien:String,
  },
  };
  export default Arti;
  </script>

  <style scoped>
  .articlePhoto{
      width: 50vw;
  }
  #objet{
      margin-top:3%;
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-bottom: 5%;
      width:80%;
      padding-bottom: 3%;
      background-color: white;
     
     
      
  }
  #container{
      background-color: #eeeeee;
      display: flex;
      justify-content: center;
      background-image: url("/img/old-newspaper-350376_1920.jpg");
  }
 
      
  
  </style>
