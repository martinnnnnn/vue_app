<template>
    <div id="Login">
        <h1>Account name</h1>
        <input type="text" v-model="account_name"/>
        <h1>Password</h1>
        <input type="text" v-model="account_password"/>
        <button v-on:click="TryLogin">Login</button>
    </div>


</template>

<script>
export default
{
    name: 'Login',
    data() {
        return {
            account_name:'',
            account_password:''
        }
    },
    methods: {
        TryLogin: function(event) {
            
        }
    }
}

</script>


<style scoped>

</style>