<template>
  <v-toolbar flat fixed class="Header">
    <v-toolbar-items>
      <v-btn flat @click="onLoadPage(home.url)" exact>
        <v-icon left>{{ home.icon }}</v-icon>
        <span>{{ home.title }}</span>
      </v-btn>
    </v-toolbar-items>
    <v-spacer/>
    <v-toolbar-items>
      <v-btn flat v-for="i in menu" :key="i.key" @click="onLoadPage(i.url)">
        <span>{{ i.title }}</span>
      </v-btn>
    </v-toolbar-items>
    <v-spacer/>
    <v-toolbar-items>
      <v-btn flat v-for="i in socialMenu" :key="i.key" :href="i.url" target="_blank">
        <v-icon>{{ i.icon }}</v-icon>
      </v-btn>
    </v-toolbar-items>
  </v-toolbar>
</template>

<script>
  export default {
    data () {
      return {
        home: { key: 'home', title: 'Studio Yehor Popov', icon: 'mdi-firebase', url: '/' },
        menu: [
          { key: 'projects', title: 'Проекты', url: '/projects' },
          { key: 'howitworks', title: 'Как мы работаем', url: '/how-it-works' },
          { key: 'works', title: 'Наши работы', url: '/works' },
          { key: 'team', title: 'Команда', url: '/team' },
          { key: 'contacts', title: 'Контакты', url: '/contacts' }
        ],
        socialMenu: [
          { key: 'facebook', icon: 'mdi-facebook', url: 'https://www.instagram.com/sentimony.records/', target: 'true' },
          { key: 'instagram', icon: 'mdi-instagram', url: 'https://www.facebook.com/sentimony.records/', target: 'true'}
        ]
      }
    },
    methods: {
      onLoadPage (url) {
        this.$router.push(url)
      }
    }
  }
</script>

<style lang="stylus">
  .Header
    //
</style>
