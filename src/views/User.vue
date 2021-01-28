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
                <img src="https://randomuser.me/api/portraits/men/10.jpg" style="max-width: 100%">
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
  </div>
</template>

<script>
// @ is an alias to /src
export default {
        name: 'User1',
        data() {
            return {
                dat: {}
            }
        },
        methods: {
            getUser() {
                this.axios
                .get("http://jsonplaceholder.typicode.com/users/1")
                .then((response) => {this.dat = response.data})
            }
        },
        mounted() {
            this.getUser();
        }
    }
</script>
