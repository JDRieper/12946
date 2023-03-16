<template>
    <div class="row justify-content-center">
        <div class="col-md-6">
            <h1>Novo Produto</h1>
            <form @submit.prevent="handleSubmitForm">
                <div class="form-group">
                    <label>Nome</label>
                    <input type="text" class="form-control" v-model="produto.nome" required>
                </div>
                <div class="form-group">
                    <label for="idade">Marca</label>
                    <input type="text" class="form-control" v-model="produto.marca" required maxlength="10">
                </div>
                <div class="form-group">
                    <label for="idade">Modelo</label>
                    <input type="text" class="form-control" v-model="produto.modelo" required maxlength="10">
                </div>
                <div class="form-group">
                    <label for="idade">Preço</label>
                    <input type="text" class="form-control" v-model="produto.preco" required maxlength="10">
                </div>
                <div class="form-group mt-3">
                    <button class="btn btn-success btn-block w-100" type="submit">Criar</button>
                </div>
            </form>
        </div>
    </div>
</template>

<script>

import axios from 'axios'

export default {
    data() {
        return {
            produto: {
                id: '',
                nome: '',
                marca: '',
                modelo: '',
                preco: ''
            }
        }
    },
    methods: {
        handleSubmitForm() {
            let apiURL = 'http://localhost:3000/contatos'

            axios.post(apiURL, this.produto).then(() => {
                alert('Produto registrado!!')
            }).catch(error => {
                console.log(error)
            })
        }
    }
}
</script>