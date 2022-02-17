<template>
    <h1>ユーザID: {{ user.name }}</h1>
</template>

<script>
// チルダでプロジェクトルートを指定できる
import users from '~/data/users.json';

export default {
    head() {
      return {
        // computedやdataの要素を使って動的にタグをつけられる
        title: this.user.name,
      };
    },
    data(){
        return {
            id: this.$route.params.id,
            users: users,
        }
    },
    computed:{
        user(){
            return this.users.find(user => user.id == this.id);
        } 
    },
    mounted() {
      // クライアント側だけで実行される
      console.log('mounted');
      console.log(this.$route);
    },
    created() {
      // サーバ側とクライアント側で実行される
      console.log('created');
      console.log(this.$route);
    }
}
</script>
