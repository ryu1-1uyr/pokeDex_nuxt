<template>
  <div>
    <b-navbar toggleable="lg" type="dark">

      <b-navbar-toggle target="nav-collapse" style="background-color: #47494e">三</b-navbar-toggle>


      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item >

            <div>
              <b-button v-b-modal.modal-1>手持ち</b-button>

              <b-modal id="modal-1" title="手持ちポケモン">
                <p class="my-4">ここに手持ちのポケモンのアイコンを表示したいね</p>
              </b-modal>
            </div>

          </b-nav-item>

        </b-navbar-nav>

        <!--ここでコンポーネント切り分けるとCSS周りがクソだるくなるのでやめた-->
        <b-navbar-nav class="ml-auto">
          <b-nav-form>

            <b-form-input list="my-list-id" v-model="pickpokemon" v-on:keydown.enter="nameToNumber(pickpokemon)" ></b-form-input>

            <datalist id="my-list-id">
              <option>Manual Option</option>
              <option v-for="pokename in pokenames" ><a @click="nameToNumber(pickpokemon)" :href="'/'+pickupnumber"></a>{{pokename }}</option>
            </datalist>

            <b-button size="sm" class="my-2 my-sm-0" @click="nameToNumber(pickpokemon)" :href="'/pokemon/'+pickupnumber">Search</b-button>
          </b-nav-form>
        </b-navbar-nav>

      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
  import Pokename from '@/assets/pokename'

    export default {
      name: "header",
      data() {
        return {
          pickpokemon: '',
          pickupnumber: 1,
          pokenames: Pokename
        }
      },
      methods: {
        nameToNumber(pokename) {
          const result = Object.keys(this.pokenames).filter((k) => { return this.pokenames[k] == pokename })[0];
          this.pickupnumber = result
          console.log(result)
        }
      },
      mounted(){
        this.pickpokemon =  Pokename[Math.floor(Math.random()*809 +1)]
      }
    }
</script>

<style scoped>

</style>
