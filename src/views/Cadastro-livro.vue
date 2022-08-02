<template>
    <div id="register">
        <div class="header-register-book">
            <h1>Cadastro livro</h1>
        </div>

        <div class="datas-books">
            <div class="input-book">
                <h2>Id do usuário dono do livro:</h2>
                <input id="name" class="input" type="text">
            </div>

            <div class="input-book">
                <h2>Nome do livro:</h2>
                <input id="owner" class="input" type="text">
            </div>

            <div class="btns">
                <button v-on:click="registerBook()">Cadastrar</button>
                <p v-on:click="back()" id="back">&#10229;</p>
            </div>
        </div>
    </div>
</template>

<script>
import api from "../services/api.js";
export default {

    methods:
    {
        registerBook: function () {
            let name = document.getElementById("name").value;
            let owner = document.getElementById("owner").value;

            api.post("/book", {
                name: name,
                id_user_owner: owner
            })
                .then((response) => {
                    alert("cadastro concluido");
                    console.log(response);
                }, (error) => {
                    alert("Erro");
                    console.log(error);
                });
        },
        back: function () {
            this.$router.push("/");
        }
    }
}
</script>

<style scoped>
.header-register-book {
    padding-top: 10px;
}

.datas-books {
    margin-top: 80px;
}

#back {
    font-size: 30px;
    position: relative;
    top: 5%;
    left: -40%;
    cursor: pointer;
}

.btns {
    margin-top: 20px;
}

button {
    border-radius: 20px;
    width: 200px;
    height: 50px;
    cursor: pointer;
}

#register {
    background-color: burlywood;
    width: 50%;
    margin-left: 25%;
    margin-right: 25%;
    height: 600px;
}

.input {
    height: 30px;
    width: 70%;
    margin-left: 15%;
    margin-right: 15%;
}
</style>