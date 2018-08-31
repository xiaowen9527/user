<template>
    <div class="login">
        <ul>
            <li>
                <label>帐号</label>
                <input type="text" v-model="username" placeholder="请输入帐号">
            </li>
            <li>
                <label>密码</label>
                <input type="password" v-model="password">
            </li>
        </ul>
        <div class="btn">
            <el-button type="primary" plain @click="goLogin">登录</el-button>
            <el-button type="primary" plain @click="goRegister">注册</el-button>
        </div>
    </div>
</template>

<script>
export default {
  name: "login",
  data() {
      return {
          username:'',
          password:''
      }
  },
  methods: {
      goLogin(){
          if(this.username.length===0){
              alert('请输入帐号')
              return false
          }else if(this.password.length===0){
              alert('请输入密码')
          }

        this.$http.post('',{
            username:this.username,
            password:this.password
        })
            .then(res=>{

                
                alert('登录成功')
                this.$router.push('/admin')
            })
            .catch(err=>{
                alert(err)
            })
    
      },
      goRegister(){
          this.$router.push('/register')
      }
  }
};
</script>

<style lang="stylus" scoped>
.login>>>.el-button
    padding 10px 15px
    margin 20px 0 0 50px
.login
    width 300px
    height 200px
    position absolute
    top 0
    bottom 0
    left 0
    right 0
    margin auto
    box-shadow 1px 1px 2px #cccccc, -1px -1px 2px #cccccc
    ul
        padding 0
        margin 10px 0 0
        li
            height 40px
            width 80%
            padding 8px 10%
            list-style none
            label
                width 15%
                line-height 40px
                font-size 16px
                text-align center
                display block
                float left
                margin-right 10px
            input
                height 30px
                margin 4px 0
                line-height 30px
                border 1px solid #cccccc
                outline none
                font-size 14px
                padding-left 10px
    .btn
        height 50px
        width 100%
    
</style>
