<template>
<div class="container">
    <h3>Users:</h3>
    <table class="table">
        <thead>
            <tr>
                <th scope="col">Id</th>
                <th scope="col">Name</th>
                <th scope="col">Email</th>
                <th scope="col">City</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="user in users" v-bind:key="user.id">
                <th scope="row">{{user.id}}</th>
                <td>{{user.username}}</td>
                <td>{{user.password}}</td>
             </tr>
          </tbody>
     </table>
 </div>
</template>
<script>
    import axios from 'axios';
    export default {
        name: 'Users',
        data() {
            return {
            users: null,
            };
        },
        created: function() {
            axios.get('http://localhost:3000/api/v1/users')
            .then(res => {
            this.users = res.data;
            })
        }
    }
</script>
<style>
h3 {
    margin-bottom: 5%;
}
</style>