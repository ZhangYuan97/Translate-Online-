<template>
  <div id="inputForm">
    <h3>在线翻译</h3>
    <form v-on:submit="formSubmit">
      <div class="form-group">
        <textarea type="text" placeholder="请输入你要翻译的内容" v-model="transtext" class="form-control" rows="10" maxlength="500"></textarea>
        <div class="pull-right">
          <select v-model="lang">
            <option value="zh">Chinese</option>
            <option value="en">English</option>
            <option value="es">Spanish</option>
            <option value="ja">Japanese</option>
            <option value="fr">French</option>
            <option value="ru">Russian</option>
            <option value="de">German</option>
            <option value="hy">Armenian</option>
            <option value="el">Greek</option>
            <option value="it">Italian</option>
            <option value="ko">Korean</option>
            <option value="la">Latin</option>
            <option value="ro">Romanian</option>
          </select>
          <input type="submit" value="翻译" class="btn btn-sm btn-default">
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'InputForm',
  data:function(){
    return{
      transtext:"",
      lang:"en",
      down:"1",
      up:""
    }
  },
  methods:{
    formSubmit(e){
      this.$emit("formSubmit", this.transtext, this.lang);//事件注册
      e.preventDefault();
    },
    choose(){
      this.down = "";
      this.up = "1";
    },
    dischoose(){
      this.down = "1";
      this.up = "";
    }
  }
}
</script>

<style>
  select {
    margin-right: -4px;
    border-radius: 3px;
    background-color: transparent;
    color: #ccc;
    height: 32px;
  }
  .btn-sm {
    background-color: transparent;
    color: #ccc;
  }
</style>
