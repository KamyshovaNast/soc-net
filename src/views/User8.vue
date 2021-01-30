<template>
  <div class="home">
        <v-row class="text-left">
            <v-col cols="10">
                <h1 class="green--text text--darken-2">
                    <v-icon large color="green darken-2">mdi-account-outline</v-icon>
                    {{dat.name}}
                </h1>
            </v-col>
        </v-row>
        <v-row class="text-left">
            <v-col cols="2">
                <img src="https://randomuser.me/api/portraits/men/8.jpg" style="max-width: 100%">
            </v-col>
            <v-col cols="10" class="text-left">
                <p>
                    Website: <a href="..." target="_blank">{{dat.website}}</a>
                </p>
                <p>
                    E-mail: <a href="mailto:...">{{dat.email}}</a>
                </p>
                <p>
                    City: {{dat.address.city}}
                </p>
                <p>
                    Workplace: {{dat.company.name}}
                </p>
            </v-col>
        </v-row>
        <v-divider></v-divider>
        <h2>Posts</h2>
        <v-container>
        <v-row>
          <v-col v-for="i in post"
            :key="i"
            cols="10">
            <v-card>
                <div class="postsHead">
                <v-avatar size="56">
                  <img class="avatar" alt="user" src="https://randomuser.me/api/portraits/men/8.jpg">
                </v-avatar>
                <div class="titl">
                    <v-card-title>{{i.title}}</v-card-title>
                    <v-card-subtitle>Author: {{dat.name}}</v-card-subtitle>
                </div>
                </div>
                <v-card-text>{{i.body}}</v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
  </div>
</template>

<script>
// @ is an alias to /src
export default {
        name: 'User2',
        data() {
            return {
                dat: {},
                post: {}
            }
        },
        methods: {
            getUser() {
                this.axios
                .get("http://jsonplaceholder.typicode.com/users/8")
                .then((response) => {this.dat = response.data})
            },
            getUserPost() {
                this.axios
                .get("http://jsonplaceholder.typicode.com/posts?userId=8")
                .then((response) => {this.post = response.data})
            },
        },
        mounted() {
            this.getUser();
            this.getUserPost();
        },
        watch: {
            $route() {
                this.getUser(),
                this.getUserPost();
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