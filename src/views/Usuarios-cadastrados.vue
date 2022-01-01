<template>
    <div id="users">
        <h1>Usuários cadastrados</h1>
        <br>
         
        <div id="names">
            <p  v-for="element in data" :key="element.name" >ID: {{element.id}} / Nome: {{element.name}} / Senha: {{element.password}}</p>
        </div>
        <p v-on:click="back()" style="font-size:30px;position:relative;top:20%;left:-40%;cursor:pointer">&#10229;</p>
    </div>
</template>
<script>
import axios from 'axios';
export default {
    data()
    {
        return{
          data: [],
     
        }
        
    },
    mounted()
    {
        
        axios
            .get('http://localhost:3000/user')
            .then((response) => 
            {
                    this.data = response.data.response;
                   
            },
            (error) =>
            {
                console.log(error);
            });
    },
    methods:
    {
        back:function()
        {
            window.location.href ="http://localhost:8080/";
        }        
    }
}
</script>
<style scoped>
#names
{
    
    border-style: solid;
    border-color:gray;
    border-width: 1px;
    
    background-color:rgb(250, 208, 153);
    width:80%;
    padding:2px;
    margin-bottom: 5px;
    margin-left:10%;
    margin-right:10%;
    
}
button
{
    border-radius:20px;
    width:200px;
    height:50px;
    cursor:pointer;
}
#users
{
    background-color:burlywood;
    width:50%;
    margin-left:25%;
    margin-right:25%;
    height:100%;
}
.input
{
    width:70%;
    margin-left:15%;
    margin-right:15%;
}
</style>