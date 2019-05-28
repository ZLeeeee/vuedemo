<template>
  <div class="hello">
    <!--vue的魔板里面所有内容都要被一个根节点包起来-->
    <h2>这是一个根组件</h2>
    <h1 ref="test">{{msg}}</h1>
    <input v-model="msg">
    <!--ref属性获取dom-->
    <input ref="aaa">
    <h1>{{obj.name}}</h1>
    <button v-on:click="getMsg()">戳我</button>
    <br>
    <button v-on:click="setMsg()">戳我</button>
    <br>
    <button v-on:click="getInputValue()">戳我</button>
    <br>
    <button @click="getInputValue()">戳我</button>
    <br>
    <!--实践对象-->
    <button @click="eventFn($event)">事件对象</button>
    <ul>
      <li v-for="item in list">
        {{item}}
      </li>
    </ul>
    <hr>
    <br>
    <ul><!--遍历数组中的变量-->
      <li v-for="item in list1">
        {{item.title}}
      </li>
    </ul>
    <hr>
    <br>
    <ul><!--遍历数组中变量的数组-->
      <li v-for="item in list2">
        {{item.cate}}
        <ol><!--带索引的遍历方式-->
          <li v-for="(a,b) in item.list">
          {{a}}===={{b}}
            <ul><!--遍历对象的属性-->
              <li v-for="c in a">
                {{c}}
              </li>
              <li v-for="(d,e) in a">
                {{d}}:{{e}}
              </li>
            </ul>
          </li>
        </ol>
      </li>
    </ul>

    <h2 v-bind:title="title">我是一个title</h2><!--v-bind绑定属性-->
    <img v-bind:src="src">
    <img :src="src"><!--简写-->

    <!--v-html绑定html-->
    <span v-html="h2"></span>

    <!--v-text绑定text-->
    <span v-text="h2"></span>

    <!--绑定class-->
    <span :class="{active: isActive,blue: !isError}">111</span>
    <hr>
    <br>
    <span :class="obj">111</span>
    <hr>
    <br>
    <ul>
      <li v-for="(item,key) in list"  :class="{blue :key==0}">
        {{key}}----{{item}}
      </li>
    </ul>
    <hr>
    <br>
    <ul>
      <li v-for="(item,key) in list" :style="styleObject">
        {{key}}----{{item}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  /*业务逻辑定义的数据*/
  /*
   *
   * 双向数据绑定mvvm
   * 只可在表单中使用
   * v-model
   */
    data(){
      return {
        styleObject: {
          color: 'red',
          fontSize: '13px'
        },
        isActive:true,
        isError:false,
        h2:"<h2>我是一个h2</h2>",
        src:"https://ss3.baidu.com/-rVXeDTa2gU2pMbgoY3K/it/u=1488861817,1113726833&fm=202",
        title:"我是一个title",
        msg:"你好vue",
        obj:{
          name:"张三",
        },
        list:["111","222","333"],
        list1:[
          {"title":"11111"},
          {"title":"22222"},
          {"title":"33333"},
          {"title":"44444"},
        ],
        list2:[
          {
            cate:"国内新闻",
            list:[
              {
                "title":"国内新闻111111"
              },{
                "title":"国内新闻22222"
              },
            ]
          },
          {
            cate:"国外新闻",
            list:[
              {
                "title":"国外新闻111111"
              },{
                "title":"国外新闻22222"
              },
            ]
          },
          {
            cate:"西安新闻",
            list:[
              {
                "title":"西安新闻111111"
              },{
                "title":"西安新闻22222"
              },
            ]
          }
        ]
      }
    },methods:{
    /*
    放方法的地方
    */

      getMsg(){
        console.log(this.msg);
    },setMsg(){
        this.msg = "我是改变后的数据";
    },getInputValue(){/**
     获取input中的value
     */


        console.log(this.$refs.aaa.value)
      this.$refs.test.style.color = 'red';
    },eventFn(e){
        //e.srcElement事件对象获取dom节点
        e.srcElement.style.color='red';
        console.log(e);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.active{
  color: red;
}
  .blue{
    color: blue;
  }
</style>
