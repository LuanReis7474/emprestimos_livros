<template>
    <div id="loan">
        <div class="header-loan">
            <h1>Emprestar Livro</h1>
        </div>

        <div class="datas-loan">
            <div class="input-loan">
                <h2>Id do livro:</h2>
                <input id="book" class="input" type="text">
            </div>

            <div class="input-loan">
                <h2>Id do usuário que vai emprestar o livro:</h2>
                <input id="user" class="input" type="text">
            </div>

            <div class="input-loan">
                <h2>Data do emprestimo:</h2>
                <input id="date" class="input" type="date">
            </div>

            <div class="btns">
                <button v-on:click="registerUser()">Concluir</button>
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
            let book = document.getElementById("book").value;
            let user = document.getElementById("user").value;
            let date = document.getElementById("date").value;
            api.post('/loan', {
                id_user_receiver: user,
                id_book: book,
                date_loan: date,
                returned: 0
            })
                .then((response) => {
                    alert("Emprestimo concluido");
                    console.log(response);
                }, (error) => {
                    alert("erro");
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
.header-loan {
    padding-top: 10px;
}

.datas-loan {
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

#loan {
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