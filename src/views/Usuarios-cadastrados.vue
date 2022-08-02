<template>
    <div id="users">
        <div class="header-users">
            <h1>Usuários cadastrados</h1>
        </div>

        <div id="names">
            <p v-for="element in data" :key="element.name">ID: {{ element.id }} / Nome: {{ element.name }} / Senha:
                {{ element.password }}</p>
        </div>

        <p v-on:click="back()" id="back">&#10229;</p>
    </div>
</template>
<script>
import api from "../services/api.js";
export default {
    data() {
        return {
            data: [],
        }
    },
    mounted() {

        api.get('/user')
            .then((response) => {
                this.data = response.data.response;

            },
                (error) => {
                    console.log(error);
                });
    },
    methods:
    {
        back: function () {
            this.$router.push("/");
        }
    }
}
</script>
<style scoped>
#back {
    font-size: 30px;
    position: relative;
    top: 20%;
    left: -40%;
    cursor: pointer;
}

.header-users {
    padding-top: 10px;
}

#names {

    border-style: solid;
    border-color: gray;
    border-width: 1px;
    background-color: rgb(250, 208, 153);
    width: 80%;
    padding: 2px;
    margin-bottom: 5px;
    margin-left: 10%;
    margin-right: 10%;
    margin-top: 20px;
}

button {
    border-radius: 20px;
    width: 200px;
    height: 50px;
    cursor: pointer;
}

#users {
    background-color: burlywood;
    width: 50%;
    margin-left: 25%;
    margin-right: 25%;
    height: 100%;
}

.input {
    width: 70%;
    margin-left: 15%;
    margin-right: 15%;
}
</style>