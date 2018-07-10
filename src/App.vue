<template>
  <div id="app">
    <h1>{{title}}</h1>
    <ul>
      <li v-for="(todo,index) in todos">
         <label> {{index+1}}.{{todo.value}} </label>
         <time>{{todo.created|date}}</time>
      </li>
    </ul>
  </div>
</template>

<script>
import moment from 'moment';
import 'moment/locale/zh-cn';
moment.locale('zh-cn');
export default {
  name: 'app',
  data(){
    return{
        title:"vue-todos",
        todos:[
          {value:"看书",done:false,created:Date.now()},
          {value:"学外语",done:true,created:Date.now()+3600000},
          {value:"编程",done:true,created:Date.now()+7200000}
        ],
    }
  },
  filters:{
    date(val){
      return moment(val).calendar()
    }
  }
}
</script>

<style>
ul{
  list-style: none;
}
</style>
