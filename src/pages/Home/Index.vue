<template>
  <v-layout>
    <v-card contextual-style="dark" v-if="show">
      <span slot="header">
        一级主页面
      </span>
      <div slot="body">主内容页</div>
      <div slot="footer" :showDate="showDate">
        <div>来自主页面</div>
        <button type="button" class="btn btn-info " @click="toggle1">去子组件并传递数据</button>
      </div>

    </v-card>
    <v-card contextual-style="dark" v-else>
      <span slot="header">
        组件主页
      </span>
      <div slot="body">组件内容页</div>
      <div slot="footer">
        <div>来自组件页面</div>
        <my-button showDate="***父组件传递的数据***" @toggleEvent="toggle"></my-button>
      </div>

    </v-card>

  </v-layout>
</template>

<script>
/* ============
 * Home Index Page
 * ============
 *
 * The home index page.
 */

import VLayout from '@/layouts/Default';
import VCard from '@/components/Card';
import MyButton from '@/components/MyButton';

export default {
  /**
   * The name of the page.
   */
  name: 'home-index',
  data() {
    return {
      show: true,
      showDate: "父子间传过来的数据"
    }
  },
  methods: {
    toggle1(){
this.show =false;
    },
    toggle(data) {
      console.log(data)
      this.show = data;
    }
  },
  mounted() {
    // this.toggle();
  },
  /**
   * The components that the page can use.
   */
  components: {
    VLayout,
    VCard,
    MyButton
  },
};
</script>
