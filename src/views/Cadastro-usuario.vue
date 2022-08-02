<template>
    <div id="register">
        <div class="header-register">
            <h1>Cadastro usuário</h1>
        </div>

        <div class="datas-user">
            <div class="input-user">
                <h2>Nome:</h2>
                <input id="name" class="input" type="text">
            </div>

            <div class="input-user">
                <h2>Senha:</h2>
                <input id="password" class="input" type="password">
            </div>

            <div class="btns">
                <button v-on:click="registerUser()">Cadastrar</button>
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
        registerUser: function () {
            let name = document.getElementById("name").value;
            let password = document.getElementById("password").value;
            api.post('user', {
                name: name,
                password: password
            })
                .then((response) => {
                    alert("cadastro concluido");
                    console.log(response);
                }, (error) => {
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
.header-register {
    padding-top: 10px;
}

.datas-user {
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