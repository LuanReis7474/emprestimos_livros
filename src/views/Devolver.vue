<template>
    <div id="loan">
        <div class="header-loan">
            <h1>Devolver livro</h1>
        </div>

        <div class="datas-loan">
            <div class="input-loan">
                <h2>Id do livro que deseja devolver:</h2>
                <input id="book" class="input" type="text">
            </div>

            <div class="btns">
                <button v-on:click="returnedBook()">Devolver</button>
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
        returnedBook: function () {

            let iDbook = document.getElementById("book").value;
            console.log(iDbook);
            api.post(`/return/${iDbook}`)
                .then((response) => {
                    console.log(response);
                    alert("Livro devolvido com sucesso");
                },
                    (error) => {
                        console.log(error);
                        alert("erro");
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
    margin-top: 120px;
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