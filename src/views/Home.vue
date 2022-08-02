<template>
    <div id="home">
        <div class="header-home">
            <h1>&#128218; Emprestimos de livros</h1>
        </div>

        <div class="list-btns">
            <div class="btns-link">
                <router-link to="/cadastro-usuario" class="list-nav">Cadastrar usuário</router-link>
            </div>

            <div class="btns-link">
                <router-link to="/cadastro-livro" class="list-nav">Cadastrar Livro para usuário</router-link>
            </div>

            <div class="btns-link">
                <router-link to="/emprestar-livro" class="list-nav">Emprestar livros para usuários</router-link>
            </div>

            <div class="btns-link">
                <router-link to="/devolver" class="list-nav">Devolver Livro</router-link>
            </div>

            <div class="btns-link">
                <router-link to="/usuarios-cadastrados" class="list-nav">Acessar informações de usuários cadastrados
                </router-link>
            </div>

            <div class="btns-link">
                <router-link to="/livro-cadastrados" class="list-nav">Acessar livros cadastrados</router-link>
            </div>

            <div class="btns-link">
                <router-link to="/lista-emprestimos" class="list-nav">Acessar informações de emprestimos</router-link>
            </div>
        </div>
    </div>
</template>

<style scoped>
.header-home {
    padding-top: 10px;
}

.list-btns {
    margin-top: 80px;
}

.btns-link {
    width: 100%;
    margin-bottom: 30px;
}

.list-nav {
    border: 1px solid black;
    border-radius: 20px;
    height: 50px;
    cursor: pointer;
    background-color: antiquewhite;
    padding: 10px;
    text-decoration: none;
    color: black;
}

#home {
    background-color: burlywood;
    width: 50%;
    margin-left: 25%;
    margin-right: 25%;
    height: 580px;
}

.input {
    width: 70%;
    margin-left: 15%;
    margin-right: 15%;
}
</style>