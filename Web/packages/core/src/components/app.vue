<template>
  <div class="dokit-app">
    <div class="dokit-entry-btn" style="z-index: 10000;" v-dragable @click="toggleShowContainer"></div>
    <div class="mask" v-show="showContainer" @click="toggleContainer"></div>
    <router-container v-show="showContainer"></router-container>
    <!-- <single-container></single-container> -->
  </div>
</template>

<script>
import dragable from "@common/directives/dragable";
import RouterContainer from './router-container';
import SingleContainer from './single-container';
import {toggleContainer} from '@store/index';

export default {
  components: {
    RouterContainer,
    SingleContainer
  },
  directives: {
    dragable,
  },
  data() {
    return {};
  },
  computed: {
    state(){
      return this.$store.state
    },
    showContainer(){
      return this.state.showContainer
    }
  },
  methods: {
    toggleShowContainer() {
      toggleContainer()
    },
  },
  created(){
    console.log("CurState: ",this.$store.state)
  }
};
</script>

<style lang="less" scoped>
.dokit-app {
  font-family: Helvetica Neue, Helvetica, Arial, sans-serif;
}
.dokit-entry-btn {
  width: 50px;
  height: 50px;
  padding: 10px;
  box-sizing: border-box;
  background-image: url(//pt-starimg.didistatic.com/static/starimg/img/OzaetKDzHr1618905183992.png);
  background-size: 50px;
  background-position: center;
  background-repeat: no-repeat;
}
.mask{
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 3;
  background-color: #333333;
  opacity: 0.3;
}
</style>