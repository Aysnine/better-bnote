<template>
  <div class="super-nav">
    <template v-for="item in menu">
      <template v-if="item.items && item.items.length>0">
        <div class="super-nav-group">
          <div class="super-nav-item" v-for="item2 in item.items">
            <router-link :to="item2.link">{{ item2.text }}</router-link>
          </div>
        </div>
      </template>
      <template v-else>
        <div class="super-nav-item">
          <router-link :to="item.link">{{ item.text }}</router-link>
        </div>
      </template>
    </template>
    <cate-list :filter='cateFilter' style="max-width: 618px; margin: auto;" />
  </div>
</template>

<script>
export default {
  name: 'SuperNav',
  computed: {
    menu() {
      return this.$themeLocaleConfig.nav
    }
  },
  methods: {
    cateFilter({ path }) {
      return path.slice(-5) === '.html'
    }
  }
}
</script>

<style lang="stylus" scoped>
.super-nav
  text-align center
  margin 20px 0
.super-nav-item
  display inline-block
  position relative
  height 50px
  line-height @height
  width 140px
  background #fff
  margin 15px 5px
  cursor pointer
  border 1px solid #eee
  border-radius 3px
  transition margin .25s
  @media (max-width 719px)
    margin 10px 5px
  a
    display block
    color inherit
    font-size 18px
    font-weight 100
    overflow hidden
    background linear-gradient(135deg, #673ab7 10px, rgba(0,0,0,0.01) 0)
    transition box-shadow .25s
    &:hover
      box-shadow 1px 1px 15px rgba(67,38,100,0.15)
</style>
