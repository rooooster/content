<template>
  <v-layout row wrap class="Hero mb-5">
    <v-flex xs4>
      <div class="HeroChoose fs24 fw800">{{ choose }}</div>
      <v-layout align-center>
        <v-flex>
          <img class="HeroUserpic" :src="userpic" alt="">
        </v-flex>
        <v-flex>
          <div class="HeroYehorpopov">{{ yehorpopov }}</div>
          <div class="HeroPosition">{{ position }}</div>
        </v-flex>
      </v-layout>
    </v-flex>
    <v-flex xs8>
      <v-layout>
        <v-flex xs4 v-for="i in data" :key="i.slug" v-if="i.homeTopImg">
          <a class="topImgItem"
            @click="onLoadProject(i.slug)"
            :style="'background-image:url(' + i.homeTopImg + ')'"
          >
            <div :class="'topImgItem__hover topImgItem__hover--' + i.slug">
              <div class="topImgItem__title">{{ i.shorttitle }}</div>
              <v-btn outline class="mx-0 mt-4">
                Подробнее
                <v-icon>mdi-chevron-right</v-icon>
              </v-btn>
            </div>
          </a>
        </v-flex>
      </v-layout>
    </v-flex>
  </v-layout>
</template>

<script>
  export default {
    data () {
      return {
        choose: 'Выберите дизайн проект, а мы сделаем перепланировку, ремонт и архитекторский надзор за 60 дней',
        userpic: 'https://images.unsplash.com/photo-1495147334217-fcb3445babd5?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=160&h=160&q=69',
        yehorpopov: 'Егор Попов',
        position: 'Главный архитектор дизайн студии'
      }
    },
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
  .Hero
    // display block
    &Choose
      // font-size: 24px
      // font-weight: 800
      margin-top: 160px
      margin-bottom: 20px
      margin-right: -50%
      position: relative;
      z-index: 1
    &Userpic
      display: block;
      width: 80px;
      height: auto;
      border-radius: 100px
    &Yehorpopov
      //
    &Position
      font-size: 12px

  .topImgItem
    display block
    min-height 460px
    position relative
    overflow hidden
    background-size cover
    background-position center bottom

    &:hover
      .topImgItem__hover
        bottom 0

    &__hover
      height 190px
      position absolute
      bottom -150px
      left 0
      width 100%
      // z-index 10
      transition: bottom .1s ease
      padding 7px 12px

      &--minimalism
        background-color #f2f2f2

      &--le-corbusier
        background-color #e8ca6a

      &--brutal-electricity
        background-color #b17629

    &__title
      font-weight 800
      color #262626
      font-size 17px


</style>
