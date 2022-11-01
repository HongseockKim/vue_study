<template>
  <div id="list">
    <p>리스트 컴포넌트 입니다.</p>
    <p>카운트 : <span class="count_num">{{count}}</span></p>
    <button class="btn" @click="clicksUpNumber()">증가</button>
    <button class="btn" @click="clicksDownNumber()">감소</button>
    <div v-show="isClickSet" class="text_content">
      <button type="button" class="close_btn" @click="closeClick()">X</button>
      <p>{{getData}}</p>
    </div>
    <div v-if="isSet">
      <ul v-for="(item,key) in listData" v-bind:key="key">
        <li ref="list_data" @click="listClick(key)"><span class="nums">{{key + 1}}</span> {{item}}</li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  data(){
    return{
      isClickSet: false,
      count: 1,
      listData: ['A_1','A_2','A_3','A_4','A_5','A_6'],
      getData: ""
    }
  },
  props: {
    isSet: Boolean,
    arrayData: Array
  },
  btnClick: function (){
    console.log(this.isSet)
  },
  methods:{
    clicksUpNumber: function() {
      this.count++;
    },
    clicksDownNumber: function() {
      this.count--;
    },
    closeClick: function (  ){
      this.isClickSet = false;
      return this.isClickSet
    },
    listClick: function (key){
      this.getData = this.$refs.list_data[key].textContent;
      this.isClickSet = true
      return this.getData;
    }
  }
}
</script>

<style scoped>
  #list ul{padding: 0;max-width:150px;margin: 0 auto;}
  #list li{list-style: none;border: solid 1px #ccc;text-align: left;}
  #list button.btn { display: inline-block;border:none;margin: 10px;padding:7px;border-radius: 6px;box-shadow: 1px  2px #4b4b4b;cursor: pointer; }
  #list button.btn:active{ cursor: grabbing; }
  #list .count_num{font-weight: bold;}
  #list .nums{display: inline-block;font-weight: bold;border: solid 1px #ccc;border-top:none;border-bottom:none;padding:5px;}
  #list .text_content{padding: 15px 0;position: relative;text-align: center;max-width:100px;margin: 0 auto;}
  #list .text_content p{text-align: center;}
  #list .text_content .close_btn{position: absolute;top:0;right: 0;padding:2px;}
</style>