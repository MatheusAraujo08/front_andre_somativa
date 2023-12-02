<script setup>

    const {data: alltarefas} = await useFetch('http://localhost:8000/tarefas?all');
    
</script>

<template>
    <div>
        <section v-for="tarefa in alltarefas.data" :key="tarefa.id">
            <h1>{{ tarefa.nome }}</h1>
            <h3>Status: {{ tarefa.idStatusFK.nome }}</h3>
            <h3>Ambiente: {{ tarefa.idAmbienteFK.nome }}</h3>
            <h3>Prazo: {{ tarefa.prazo }}</h3>
            <NuxtLink :to="`/tarefas/${tarefa.id}`">
                <button>
                    Detalhes
                </button>    
            </NuxtLink>
        </section>
    </div>
</template>