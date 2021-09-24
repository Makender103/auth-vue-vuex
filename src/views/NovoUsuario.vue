<template>
    <div class="container">
        <form @submit.prevent="enviarFormulario">
            <div class="form-group">
                <label for="nome">Nome</label>
                <input 
                    type="text"
                    class="form-control"
                    v-model="usuario.nome"
                >
            </div>

            <div class="form-group">
                <label for="email">email</label>
                <input
                    type="email"
                    class="form-control"
                    v-model="usuario.email"
                >
            </div>

            <div class="form-group">
                <label for="senha">senha</label>
                <input
                    type="password"
                    class="form-control"
                    v-model="usuario.senha"
                >
            </div>
            <button class="btn btn-success" type="submit">Enviar</button>
        </form>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    data: function() {
        return {
            usuario: {
                nome: '',
                senha: '',
                email: ''
            }
        }
    },
    methods: {
        enviarFormulario: function () {
            axios.post('http://localhost:8000/auth/register', this.usuario)
                .then(resposta => {
                    console.log(resposta)
                    this.$router.push({ name: 'login' })
                })
                .catch(erro => console.log(erro))
        }
    }
}
</script>