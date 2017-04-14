<template>
  <div id="app">
    <div class="container">
        <router-view></router-view>
    </div>
  </div>
</template>

<script>
import {WebStorageCache} from 'lib/StorageCache'
import store from 'store/index'
export default {
  store,
  name: 'app',
  created(){
  	//解决移动端click事件300ms的延迟响应
    $(function() {
        FastClick.attach(document.body);

        checkAuth(function(){
        	let accountName = getArgs("accountName") || getLocalData("currentAN");
        	if(!accountName){
        		console.error("没有accountName");
        	}
        	WebStorageCache.set("spid", accountDic[accountName]);
        });
    });
  }
}
</script>