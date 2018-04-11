<template>
    <div class="hello">
      
    </div>
</template>

<script>
import { MessageBox } from 'mint-ui'
export default {
	name: 'index',
	data () {
		return {
		}
	},
	created(){
		
		
	},
	methods: {
		// 登陆
		getData(){
		  let that = this
		  let landMobile = $("[name='mobile']")
		  let landPassword = $("[name='password']")
		  $.ajax({
		      url: 'http://stock.hbliangyun.cn/api/index/login',
		      data: {
		          mobile: landMobile.val(),
		          password: landPassword.val()
		      },
		      dataType: 'JSON',
		      async: false,//请求是否异步，默认为异步
		      type: 'post',
		      success: function (data) {
		        if(data.code === 1){
		          localStorage.setItem('token',data.data.token)
		          that.$router.push({ path:'/transaction/index'})
		        }else{
		          if(data.code === 0){
		            MessageBox.alert(data.msg)
		          }
		        }
		      },
		      error: function (err) {
		        
		      }
		  })
		}
	}
}
</script>


<style scoped>
</style>
