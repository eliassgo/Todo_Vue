<script setup>
const props = defineProps(['tarefas', 'quantDeTarefas']);
</script>

<template>
    <!-- Fazer uma edição para se a lista estiver vazia, aparecer uma mensagem dizendo não existe tarefas -->
    <div v-if="quantDeTarefas > 0">
        <ul class="list-group mt-4">
            <!-- v-for, que permite renderizar listas de elementos com base em uma matriz de dados.-->
            <li class="list-group-item" v-for="tarefa in props.tarefas">
                <input @change="evento => tarefa.finalizada = evento.target.checked" type="checkbox"
                    :checked="tarefa.finalizada" :id="tarefa.titulo">
                <label :class="{ done: tarefa.finalizada === true }" class="ms-3" :for="tarefa.titulo">{{ tarefa.titulo
                }}</label>
            </li>
        </ul>
    </div>
    <div v-else class="messagem">
        <h2>Lista de tarefas vazia <i class="bi bi-check2-square"></i></h2>
    </div>
</template>
<style scoped>
.done {
    text-decoration: line-through;
}

.messagem {
    margin-top: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
}

h2 {
    margin-top: 15px;
    text-align: center;
}
</style>
