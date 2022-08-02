<template>
    <div id="books">
        <div class="header-books">
            <h1>Livros cadastrados</h1>
        </div>

        <div id="names">
            <p v-for="element in data" :key="element.name">ID: {{ element.id }} / Nome: {{ element.name }} / ID do dono
                do
                livro: {{ element.id_user_owner }}</p>
        </div>

        <p v-on:click="back()" id="back">&#10229;</p>
    </div>
</template>

<script>
import api from "../services/api.js";
export default {
    data() {
        return {
            data: []
        }

    },
    mounted() {
        api.get('/book')
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
    top: 40%;
    left: -40%;
    cursor: pointer
}

.header-books {
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

#books {
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