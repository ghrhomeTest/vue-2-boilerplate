<template>
  <v-layout>
    <v-card contextual-style="dark" v-if="show">
      <span slot="header">
        一级主页面
      </span>
      <div slot="body">主内容页
        <!-- <div v-for="item in listTittle" :key="item.id">{{item}}</div>         -->
        <!-- <div v-for="item in list" :key="item.id">
            <p>{{listTittle}}{{item.name }}</p>
          </div> -->
        <div>
          <ul>
            <li>需求：{{lists.demand}}</li>
            <li>用户：{{lists.user}}</li>
            <li>时间：{{lists.time}}</li>
          </ul>
        </div>
      </div>
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
<button @click="details()">去详情页面</button>
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
      showDate: "父子间传过来的数据",
      lists: {
        demand: [],
        user: [],
        time: []
      },
      list: [{ id: 1, name: '需求1', code: 'admin.demand' },
      { id: 2, name: '需求2', code: 'admin.demand' },
      { id: 3, name: '用户1', code: 'admin.user' },
      { id: 4, name: '用户2', code: 'admin.user' },
      { id: 5, name: '时间1', code: 'admin.time' },
      { id: 6, name: '时间2', code: 'admin.time' },
      { id: 7, name: '用户3', code: 'admin.user' },]
    }
  },
  methods: {
    toggle1() {
      this.show = false;
    },
    toggle(data) {
      console.log(data)
      this.show = data;
    },
    details(){
      const userId = 123
      // this.$router.push({ path: `/details/${userId}` }) 
     this.$router.push({name:'details.index', query:{
       id:45,
       data:this.showDate
     }})
    },
    listinfo() {

      this.list.map((x) => {
        console.log(x.code.split(".")[1])
        switch (x.code.split(".")[1]) {
          case "demand":
            this.lists.demand.push(x.name);
            // 执行代码块 1
            break;
          case "user":
            // 执行代码块 2
            this.lists.user.push(x.name);
            break;
          case "time":
            // 执行代码块 3
            this.lists.time.push(x.name);
            break;
          default:

        }
      })
    }
  },
  mounted() {
    // this.toggle();
    this.listinfo();
  },
  /**
   * The components that the page can use.
   */
  components: {
    VLayout,
    VCard,
    MyButton
  },
    watch:{
        $route(to, from) {  
                console.log(to);  
                console.log(from);  
            } 
    }
};
</script>
