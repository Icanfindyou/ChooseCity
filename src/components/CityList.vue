<template>
  <div class="lists">
    <div v-for="citys in citylist" :key="citys[0]" :dataNum="citys[1].length">
      <p class="city-title" :ref="citys[0]">{{citys[0]}}</p>
      <p :class="{'city-item':true, 'vue-1px-t':index}" v-for="(city,index) in citys[1]" :key="city.id" @click="changeCity(city.name)">{{city.name}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CityList',
  props: {
    citylist: Array,
    cityIndexList: Array,
    elementIndex: String
  },
  methods: {
    changeCity (name) {
      this.$emit('positionCity', name);
    }
  },
  watch: {
    elementIndex (val) {
      if (!val) return;
      if (val === '顶') return;
      this.$emit('singleLetter', this.$refs[val][0]);
    }
  }
};
</script>

<style lang="stylus" scoped>
@import '../common/stylus/1px.css'
.lists
  width 100%
  background #fff
  div
    .city-title
      height 30px
      background #f0efed
      line-height 29px
      padding-left 10px
      box-sizing border-box
    .city-item
      margin 0px 10px
      height 35px
      line-height 35px
      box-sizing border-box
    .city-item:last-child
      border none
</style>
