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

        </b-navbar-nav>gs

        <!--ここでコンポーネント切り分けるとCSS周りがクソだるくなるのでやめた-->
        <b-navbar-nav class="ml-auto">
          <b-nav-form>
            <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
            <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
          </b-nav-form>
        </b-navbar-nav>

      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
  // import Search from '@/components/search'

    export default {
      name: "header",
    }
</script>

<style scoped>

</style>
