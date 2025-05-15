<!-- Existe tambem a forma longa, que é com   export default { setup(){} return{} }   (e sem o 'setup' no script) -->

<script lang="ts" setup>
    import { onMounted, ref } from 'vue';
    import { defineProps } from 'vue';


    // primeira forma de usar props
    const props = defineProps({
        propMessage: {
            type: String,
            default: 'abadabadul padrao valor default',
        },
        active: {
            type: Boolean,
            required: true,
        }
    })

    // segunda forma de usar props
    // type Props = {
    //     propMessage?: string
    // }
    // const props = defineProps<Props>();

    // terceira forma de usar props (como a primeira, mas com valores padrao)
    // const props = withDefaults(defineProps<Props>(), {
    //     propMessage: true
    // })


    const status = ref<boolean>(false);
    const tasks = ref<string[]>([
        'task 01',
        'task 02',
        'task 03'
    ]);
    const newTaskName = ref<string>('');

    const handleClickAlterarStatus: () => void = () => {
        status.value = !status.value;
    }

    function onChangeNewTaskName(event: Event): void{
        const target = event.target as HTMLInputElement;
        newTaskName.value = target.value;
    }

    const addTask = () => {
        tasks.value.push(newTaskName.value)
        console.log('asdsad')
    }

    onMounted(async () => {
        try {
            const response = await fetch('https://jsonplaceholder.typicode.com/todos');
            const data = await response.json();
            tasks.value = data.slice(0, 15).map( (item) => {return item.title} );
        }
        catch (error) {
            console.error(error);
        }
    })
</script>


<template>
    <h1>Composition API Component</h1>

    <div id="main-container">
        <div>
            <p>Status:</p>
            <p>{{ status }}</p>
        </div>

        <div>
            <p>Mensagem passada por Prop: <strong>{{ props.propMessage }}</strong></p>
            <p>//</p>
            <p>Segundo prop, active: <strong>{{ props.active }}</strong></p>
        </div>

        <div>
            <p>Tasks:</p>
            <ol>
                <li v-for="(task, index) in tasks" :key="index">{{ task }}</li>
            </ol>
        </div>

        <button @click="handleClickAlterarStatus">Alterar Status</button>

        <!-- esse prevent ja automatiza o event.preventDefault() do JS HTML -->
        <form v-on:submit.prevent="addTask">
            <input type="text" id="newTaskAuto"  v-model="newTaskName" placeholder="Modelo Automatico"> <!-- modelo com funcao de onChange automatica -->
            <input type="text" id="newTaskManual" :value="newTaskName" @input="onChangeNewTaskName" placeholder="Modelo Manual" /> <!-- modelo com funcao de onChange definida manualmente -->
            <p>{{ newTaskName }}</p>
            <button type="submit">Create New Task</button>
        </form>
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

        ul, ol{
            padding-left: 20px;
        }

        form{
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
    }
</style>