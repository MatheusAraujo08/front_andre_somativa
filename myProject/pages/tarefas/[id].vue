<script setup>
    const route = useRoute();
    const {data: tarefa} = await useFetch(`http://localhost:8000/tarefas/${route.params.id}`,{
        key: 'tarefasRequest'
    });
    const {data: tarefasUsuarios} = await useFetch(`http://localhost:8000/tarefasUsuarios?tarefa=${route.params.id}`,{
        key: 'tarefasUsuariosRequest'
    });
    const {data: tarefaStatus} = await useFetch(`http://localhost:8000/tarefasStatus?tarefa=${route.params.id}`,{
        key: 'tarefaStatusRequest'
    });
    
</script>

<template>
    <div>
        <h1>{{ tarefa.data.nome }}</h1>
        <h3>Status: {{ tarefa.data.idStatusFK.nome }}</h3>
        <h3>Ambiente: {{ tarefa.data.idAmbienteFK.nome }}</h3>
        <h3>Prazo: {{ tarefa.data.prazo }}</h3>
        <h3>Data inicío: {{ tarefa.data.dataInicio }}</h3>
        <h3>Data do termino: {{ tarefa.data.dataFim }}</h3>
        <p>Descricao: {{ tarefa.data.descricao }}</p>
        <h3>Nome do solicitante; {{  tarefa.data.idSolicitanteFK.nome }}</h3>
        <h3>Foto do solicitante: </h3>
        <img :src="tarefa.data.idSolicitanteFK.image" alt="Imagem da pessoa que solicitou a tarefa">

        <section v-for="Usuarios in tarefasUsuarios.data" :key="Usuarios.id">
           <h1>Nome: {{ Usuarios.idUsuarioFK.nome }}</h1>
           <h1>Image: </h1>
           <img :src="Usuarios.idUsuarioFK.image" alt="Imagem do responsavel">
        </section>
        <section v-for="Status in tarefaStatus.data" :key="Status.id">
            <h1>Status: {{ Status.idStatusFK.nome }}</h1>
            <h1>Data: {{ Status.data }}</h1>
        </section>


    </div>
</template>