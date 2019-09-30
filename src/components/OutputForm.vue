<template>
  <div id="outputform">
    <div>
    	<h3>翻译结果</h3>
    	<div class="showDiv">
    		<textarea cols="30" rows="10" class="form-control" v-bind:value="result" id="input"></textarea>
				<!-- {{ result }} -->
    	</div>
    	<div class="pull-right">
    		<button class="glyphicon glyphicon-book btn btn-default paste" @click="getPaste"></button>
    	</div>
    	
    </div>
  </div>
</template>

<script>
export default {
  name: 'OutputForm',
  props:["result"],
  methods:{
  	getPaste(){
  		document.querySelector('#input').select();
			document.execCommand('copy');
  	}
  }
}
</script>

<style>

</style>
