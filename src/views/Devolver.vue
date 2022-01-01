<template>
    <div id="cadastro">
        <br>
        <h1>Devolver livro</h1>
        <br>
        <br>
        <br>
        <h2>Id do livro que deseja devolver:</h2>
        <input id="book" class="input" type="text">
        <br>
        <br>
        <br>
        <button v-on:click="returnedBook()">Devolver</button>
        <p v-on:click="back()" style="font-size:30px;position:relative;top:10%;left:-40%;cursor:pointer">&#10229;</p>
    </div>
</template>
<script>
import axios from 'axios';
export default {
    data()
    {
        return{
            data:[]
        }
        
    },
    methods:
    {
        returnedBook: function()
        {
            
            let iDbook = document.getElementById("book").value;
            alert(iDbook);
            axios
                .get(`http://localhost:3000/return/${iDbook}`)
                .then((response) => 
                {
                        console.log(response);
                        alert("Livro devolvido com sucesso");
                },
                (error) =>
                {
                    console.log(error);
                });
        },
    
        back:function()
        {
            window.location.href ="http://localhost:8080/";
        }        
    
    }
}
</script>
<style scoped>
button
{
    border-radius:20px;
    width:200px;
    height:50px;
    cursor:pointer;
}
#cadastro
{
    background-color:burlywood;
    width:50%;
    margin-left:25%;
    margin-right:25%;
    height:500px;
}
.input
{
    height:30px;
    width:70%;
    margin-left:15%;
    margin-right:15%;
}
</style>