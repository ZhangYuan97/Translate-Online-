<template>
  <div id="app">
    <div id="wrapper">
        <div class="overlay"></div>
        <!-- Sidebar -->
        <nav class="navbar navbar-inverse navbar-fixed-top" id="sidebar-wrapper" role="navigation">
            <ul class="nav sidebar-nav">
                <li class="sidebar-brand">
                    <a href="#">
                       Alice
                    </a>
                </li>
                <li>
                    <a href="#"><i class="fa fa-fw fa-home"></i> 使用指南</a>
                </li>
                <li>
                    <a href="#"><i class="fa fa-fw fa-folder"></i> 隐私权和使用条款</a>
                </li>
            </ul>
        </nav>
        <!-- /#sidebar-wrapper -->

        <!-- Page Content -->
        <div id="page-content-wrapper">
          <button type="button" class="hamburger is-closed animated fadeInLeft" data-toggle="offcanvas">
            <span class="hamb-top"></span>
            <span class="hamb-middle"></span>
            <span class="hamb-bottom"></span>
          </button>

          <div class="container">
            <div class="row">
              <div class="col-md-6">
                <InputForm v-on:formSubmit="getInputText"></InputForm>
              </div>
              <div class="col-md-6">
                <OutputForm v-bind:result="result"></OutputForm>
              </div>
            </div>
          </div>
        </div>
        <!-- /#page-content-wrapper -->
    </div>

    
  </div>
</template>

<script>
import InputForm from './components/InputForm'
import OutputForm from './components/OutputForm'
export default {
  name: 'App',
  data:function(){
    return{
      result:""
    }
  },
  methods:{
    getInputText(text, lang){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190929T080118Z.4d67d1a58a417067.bc7ee7d17c7ba88f7b74ef8c638e35925339d6c5&lang='+lang+'&text='+text).then((response)=>{
        this.result = response.body.text[0];
      })
    }
  },
  created(){
    $(document).ready(function () {
      var trigger = $('.hamburger'),
          overlay = $('.overlay'),
         isClosed = false;

        trigger.click(function () {
          hamburger_cross();      
        });

        function hamburger_cross() {

          if (isClosed == true) {          
            overlay.hide();
            trigger.removeClass('is-open');
            trigger.addClass('is-closed');
            isClosed = false;
          } else {   
            overlay.show();
            trigger.removeClass('is-closed');
            trigger.addClass('is-open');
            isClosed = true;
          }
      }
      
      $('[data-toggle="offcanvas"]').click(function () {
            $('#wrapper').toggleClass('toggled');
      });  
    });
  },
  components: {
    InputForm,
    OutputForm
  }
}
</script>

<style>
  @import "./assets/style.css";
  @import "./assets/htmleaf-demo.css";
</style>
