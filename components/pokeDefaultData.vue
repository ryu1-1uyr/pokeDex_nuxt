<template>
    <div>きそでーただよ！！
      <p>{{name+number+abilities+types}}</p>
    </div>
</template>

<script>
    export default {
      props: {
        name: {
        },
        number: {
        },
        abilities:{
        },
        types: {
        }
      },
        name: "showDefaultData"
    }
</script>

<style scoped>

</style>
