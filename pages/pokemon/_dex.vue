<template>
    <div>
      <p>くわしいぺーじ</p>

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
        pokeName: '',
        pokeNumber: '',
        pokeAbility: '',
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
      console.log($nuxt.$route.params.dex)
    }

  }
</script>

<style scoped>

</style>
