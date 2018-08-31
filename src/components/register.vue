<template>
    <div class="register">
        <ul>
            <li>
                <label>帐号</label>
                <input type="text" v-model="username" placeholder="请输入帐号">
            </li>
            <li>
                <label>密码</label>
                <input type="password" v-model="password">
            </li>
            <li>
                <label class="dbpass">重复密码</label>
                <input type="password" v-model="dbpass">
            </li>
        </ul>
        <div class="btn">
            <el-button type="primary" plain @click="goLogin">返回登录</el-button>
            <el-button type="primary" plain @click="goRegister">确定</el-button>
        </div>

    </div>
</template>

<script>
export default {
  name: "register",
  data() {
    return {
          username:'',
          password:'',
          dbpass:''
    };
  },
  mounted() {
      console.log(this.user);
      
  },
  methods: {
    goLogin() {
     this.$router.push("/");
    },
    goRegister() {
      
        if(this.password!==this.dbpass){
            console.log(0);
            return false
        }else{
            this.$http.post('',{
                username:this.username,
                password:this.password
            })
                .then(res=>{
                    console.log(red);
                    alert('注册成功')
                    this.$router.push('/login')
                })
                .catch(err=>{
                    alert(err)
                })
        }
    

    }
  }
};
</script>

<style lang="stylus" scoped>
.register>>>.el-button
    padding 10px 15px
    margin 20px 0 0 50px
.register
    width 350px
    height 250px
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
                width 70px
            input
                height 30px
                margin 4px 0
                line-height 30px
                border 1px solid #cccccc
                outline none
                font-size 14px
                padding-left 10px
                width 140px
    .btn
        height 50px
        width 100%
</style>
