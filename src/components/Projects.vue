<template>
  <v-layout row wrap class="Projects mb-5" id="projects">
    <!-- <v-flex xs12> -->
      <v-layout row wrap class="ProjectsItem mb-5" v-for="i in data" :key="i.slug">
        <v-flex xs12>
          <div class="fs24 fw800 mb-5">{{ i.title }}</div>
        </v-flex>
        <v-flex xs4>
          <div class="ProjectsItemText mb-5">
            <div class="mb-4" v-html="i.description"/>
            <div class="mb-4">Цена проекта и ремонта: <b>{{ i.price }}</b></div>
            <v-btn outline @click="onLoadProject(i.slug)" class="mx-0">
              Подробнее
              <v-icon>mdi-chevron-right</v-icon>
            </v-btn>
          </div>
        </v-flex>
        <v-flex xs8>
          <img :src="i.img" alt="" class="ProjectsItemImg mb-5">
        </v-flex>
        <v-flex xs12>
          <img :src="i.imgSlim" alt="" class="ProjectsItemImg mb-5">
        </v-flex>
      </v-layout>
    <!-- </v-flex> -->
  </v-layout>
</template>

<script>
  export default {
    props: [
      'data'
    ],
    methods: {
      onLoadProject (slug) {
        this.$router.push('/project/' + slug)
      }
    }
  }
</script>

<style lang="stylus">
  .Projects
    // display block

    &Item
      //

      &Text
        margin: 0 40px 0 0

      &Img
        width: 100%
        display: block

      &:nth-child(2n)

        & .flex

          &:nth-child(1)
            order: 0

          &:nth-child(2)
            order: 2

          &:nth-child(3)
            order: 0

          &:nth-child(4)
            order: 3

        & .ProjectsItemText
          margin: 0 0 0 40px
</style>
