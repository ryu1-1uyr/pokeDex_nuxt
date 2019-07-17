<template>
    <div>
      <p>卍くわしいぺーじ卍</p>
      <p>{{this.pokeNumber+' : '+this.pokeName}}</p>
      <p>{{this.pokeTypes}}</p>

      <Skills />
      <DefaultData />
      <Effort />
      <Graph />

    </div>
</template>

<script>
  import Skills from '@/components/pokeSkills'
  import DefaultData from '@/components/pokeDefaultData'
  import Effort from '@/components/pokeEffortData'
  import Graph from '@/components/pokeGraph'
  import Pokename from '@/assets/pokename'
  import axios from "axios";

  export default {
    components: {
      Skills,
      DefaultData,
      Effort,
      Graph
    },
    name: "_dex",
    data () {
      return {
        baseurl: 'https://pokeapi.co/api/v2/pokemon/',
        pokeName: '',
        pokeNumber: '',
        pokeAbility: '',
        pokeTypes: [],
        pokeIndividualValue: {
          HP: '',
          Attack: '',
          Defense: '',
          SpecialAttack: '',
          SpecialDefense: '',
          Speed: ''
        }

      }
    },
    mounted(){
      this.pokeNumber = $nuxt.$route.params.dex

      console.log($nuxt.$route.params.dex,axios)
    }

  }
</script>

<style scoped>

</style>
