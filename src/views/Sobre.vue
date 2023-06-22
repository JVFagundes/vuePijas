<template>
  <div id="pijas">
    <h1 class="title">Personagens pijack</h1>
    <div class="card" v-for="p in personagens" :key="p.id">
      <div class="detalhes">
        <img class="images" :src="p.thumbnail.path + '.' + p.thumbnail.extension" alt="pijas">
        <h2 class="name">{{ p.name }}</h2>
      </div>
      <p class="descrip">{{ p.description }}</p>
    </div>
  </div>
</template>
<script>

import md5 from 'md5'
import axios from 'axios'

export default {
    name: 'sobre-view',
    data(){
        return{
            ts: Date.now(),
            publicKey: '20d8659713931a917eb3a9e9da5478ee',
            privateKey: '8160e8d06f51b6d16c1012bb9ca926d63a056613',
            hash: md5(this.ts+this.privateKey+this.publicKey),
            personagens: []
        }
    },
    mounted(){
        axios.get("https://gateway.marvel.com/v1/public/characters?ts="+this.ts+"&apikey="+this.publicKey+"&hash="+md5(this.ts+this.privateKey+this.publicKey))
        .then(res => {
            console.log(res)
            this.personagens = res.data.data.results
        })  
    }
}

</script>

<style scoped>

#pijas {
  max-width: 50rem;
  margin: 0 auto;
  padding: 20px;
}

.title {
  font-size: 30px;
  font-weight: bold;
  margin-bottom: 20px;
}

.card {
  margin-bottom: 20px;
  background-color: #f5f5f5;
  border-radius: 5px;
  padding: 10px;
}

.detalhes {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

.images {
  width: 150px;
  height: 150px;
  object-fit: cover;
  border-radius: 50%;
}

.name {
  font-size: 24px;
  margin-left: 10px;
}

.descrip {
  font-size: 18px;
  text-align: justify;
}

</style>
