<template>
    <div>
      <p>卍くわしいぺーじ卍</p>

      <DefaultData :name="this.pokeName" :number="this.pokeNumber" :abilities="this.pokeAbilities" :types="this.pokeTypes"  />
      <Effort :pokeIndividualValue="this.pokeIndividualValue" />
      <Graph :pokeIndividualValue="this.pokeIndividualValue"/>
      <Skills :moves="this.pokeMoves" />

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
        pokeAbilities: [],
        pokeTypes: [],
        pokeMoves: [],
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
    async mounted(){
      this.pokeNumber = $nuxt.$route.params.dex
      this.pokeName = await Pokename[this.pokeNumber]
      console.log(this.pokeName,Pokename[this.pokeNumber],this.pokeNumber)
      const response = await axios.get(`https://pokeapi.co/api/v2/pokemon/${this.pokeNumber}`)
      response.data.types.map(x=>{this.pokeTypes.push(x.type.name)})
      response.data.abilities.map(x=>{this.pokeAbilities.push(x.ability.name)})
      this.pokeMoves = response.data.moves

      response.data.stats.map((x)=>{
        console.log(x.stat.name+' : '+x.base_stat)
        switch (x.stat.name) {

          case 'speed':
            this.pokeIndividualValue.Speed = x.base_stat
            console.log('S : '+this.pokeIndividualValue.Speed)
            break

          case 'special-defense':
            this.pokeIndividualValue.SpecialDefense = x.base_stat
            console.log('D : '+this.pokeIndividualValue.SpecialDefense)
            break

          case 'special-attack':
            this.pokeIndividualValue.SpecialAttack = x.base_stat
            console.log('C : '+this.pokeIndividualValue.SpecialAttack)
            break

          case 'defense':
            this.pokeIndividualValue.Defense = x.base_stat
            console.log('B : '+this.pokeIndividualValue.Defense)
            break

          case 'attack':
            this.pokeIndividualValue.Attack = x.base_stat
            console.log('A : '+this.pokeIndividualValue.Attack)
            break

          case 'hp':
            this.pokeIndividualValue.HP = x.base_stat
            console.log('H : '+this.pokeIndividualValue.HP)
            break

        }
      })



    }

  }
</script>

<style scoped>

</style>
