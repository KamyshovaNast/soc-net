<template>
  <div class="users">
    <v-container>
        <v-row>
          <v-col v-for="i in users"
            :key="i"
            cols="5">
            <v-card>
                <div class="postsHead">
                <v-avatar size="56">
                  <img class="avatar" alt="user" v-bind:src="'https://randomuser.me/api/portraits/men/' + i.id + '.jpg'">
                </v-avatar>
                <div class="titl">
                    <v-card-title>{{i.name}}</v-card-title>
                    <v-card-subtitle>{{i.address.city}}</v-card-subtitle>
                </div>
                </div>
                <v-card-actions><router-link v-bind:to="'/users/' + i.id">Go to profile</router-link></v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
  </div>
</template>

<script>
// @ is an alias to /src
export default {
        name: 'Users',
        data() {
            return {
                users: {}
            }
        },
        methods: {
            getUsers() {
                this.axios
                .get("http://jsonplaceholder.typicode.com/users")
                .then((response) => {this.users = response.data})
            }
        },
        mounted() {
            this.getUsers();
        },
        watch: {
            $route() {
                this.getUsers()
            }
        }
    }
</script>


<style>
    .postsHead {
        padding: 10px;
        display: flex;
    }
    .titl {
        margin-top: -16px!important;
    }
</style>