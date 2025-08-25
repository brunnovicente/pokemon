<script setup>

  import {onMounted, ref} from "vue";

  //Exibir carregamento
  let carregou = ref(false);
  let busca = ref('')
  let vetor = ref([])

  onMounted(async ()=>{
    for(let i = 1; i < 152; i++){
      let requisicao = await fetch('https://pokeapi.co/api/v2/pokemon/'+i)
      let pokemon = await requisicao.json()
      vetor.value.push(pokemon)
      console.log(i)
    }//Fim do for
    carregou.value = true;
  })

  function filtrar(){
    return vetor.value.filter(obj => obj.name.toLowerCase().includes(busca.value.toLowerCase()))
  }

</script>

<template>
  
  <div class="mx-auto" v-if="!carregou">
    <img src="../complementos/caregamento.gif" alt="" class="d-block mx-auto">
  </div>
  
  <main class="container" v-if="carregou">
    <h3 class="text-center mt-2">Pokemons 1ª Geração</h3>
    <div class="row">
      <div class="col-12">
        <input type="text" v-model="busca" class="form-control mt-3" placeholder="Qual pokemon você está procurando?">
        <p v-if="filtrar().length == 0" class="mt-2">Não foi encontrado nenhum Pokemon.</p>
        <p v-if="filtrar().length == 1" class="mt-2">Foi encontrado apenas 1 (um) Pokemon.</p>
        <p v-if="filtrar().length > 1" class="mt-2">Foram encontrados {{filtrar().length}} Pokemons.</p>
      </div>
    </div>

    <div class="row">
      <div class="col-12 col-sm-6 col-md-4 col-lg-3" v-for="pokemon in filtrar()">
        <div class="card" :class="pokemon.types[0].type.name">
          <img :src="pokemon.sprites.other.home.front_default">
          <h1>{{pokemon.name}}</h1>
        </div>
      </div>
    </div>
  </main>

</template>

<style scoped>
  .card{
    margin-top: 30px;
    transition: transform 0.5s;
    text-align: center;
  }
  .card h1{
    font-size: 16px;
    margin-top: 10px;
  }
  .card:hover{
    transform: scale(1.1, 1.1);
  }
  .grass{
    background-color: rgb(92, 184, 92) !important;
  }

  .fire{
    background-color: rgb(188, 89, 89) !important;
  }

  .water{
    background-color: rgb(51, 58, 187) !important;
  }

  .bug{
    background-color: rgb(165, 188, 89) !important;
  }

  .normal{
    background-color: rgb(227, 227, 227) !important;
  }

  .poison{
    background-color: rgb(93, 73, 167) !important;
  }

  .ground{
    background-color: rgb(153, 122, 65) !important;
  }

  .fairy{
    background-color: rgb(167, 94, 175) !important;
  }

  .electric{
    background-color: rgb(245, 237, 86) !important;
  }

  .fighting{
    background-color: rgb(174, 166, 118) !important;
  }

  .psychic{
    background-color: rgb(130, 19, 182) !important;
  }

  .rock{
    background-color: rgb(91, 83, 64) !important;
  }

  .ghost{
    background-color: rgb(88, 74, 95) !important;
  }

  .ice{
    background-color: rgb(24, 167, 195) !important;
  }

  .dragon{
    background-color: rgb(236, 162, 0) !important;
  }

  .dark{
    background-color: rgb(85, 85, 85) !important;
  }

  .steel{
    background-color: rgb(119, 119, 119) !important;
  }
</style>