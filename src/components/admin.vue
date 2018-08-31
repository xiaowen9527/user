<template>
    <div class="admin">
        <p>帐号：{{this.username}}</p>
        <p>密码：{{this.password}}</p>
    </div>
</template>

<script>
import { mapState } from "vuex";
    export default {
        name:"admin",
        computed: {
            ...mapState(['username','password'])
        }
    }
</script>

<style scoped>

</style>