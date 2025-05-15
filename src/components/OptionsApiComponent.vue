<script lang="ts">
    export default {
        data() {
            return({
                name: 'Gustavo',
                status: false,
                foods: [
                    'apple',
                    'cookies',
                    'rice'
                ],
                link: 'https://www.google.com.br'
            })
        },
        methods: {
            handleClickAlterarStatus() {
                this.status = !this.status
            }
        }
    }
</script>


<template>
    <h1>Options API Component</h1>

    <div id="main-container">
        <div>
            <p>Name:</p>
            <p>{{ name }}</p>
        </div>

        <div>
            <p>Status:</p>
            <p>{{ status }}</p>
        </div>

        <!-- <button v-on:click="handleClickAlterarStatus">Alterar Status</button> -->
        <button @click="handleClickAlterarStatus">Alterar Status</button>

        <div v-if="status">
            <p>Esse parágrafo só é mostrado se o status for <strong>true</strong></p>
        </div>

        <div v-else="status">
            <p>Esse parágrafo só é mostrado se o status <strong>não for true</strong></p>
        </div>

        <div v-if="name === 'Gustavo'">
            <p>Esse parágrafo só é mostrado se o nome for <strong>'Gustavo'</strong></p>
        </div>

        <ul>
            <li v-for="food in foods" :key="food">{{ food }}</li>
        </ul>

        <!-- <a v-bind:href="link" rel="noreferrer" target="_blank">Link com âncora dinamica</a> -->
        <a :href="link" rel="noreferrer" target="_blank">Link com âncora dinamica</a>
    </div>
</template>


<style scoped>
    #main-container{
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        gap: 10px;

        & > div{
            display: flex;
            gap: 5px;
            align-items: center;
        }

        button{
            background-color: lightblue;
            border-radius: 3px;
            padding: 10px;

            &:hover{
                cursor: pointer;
            }
        }

        ul{
            padding-left: 20px;
        }
    }
</style>