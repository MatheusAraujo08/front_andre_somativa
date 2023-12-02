<script setup>

    const {data: allambientes} = await useFetch('http://localhost:8000/ambientes?all');
    let nome;
    await useFetch('http://localhost:8000/ambientes/',{
            method: 'POST',
            body: JSON.stringify([{"nome": nome}]),
            key: 'ambientePost'            
        });

       
    

</script>

<template>
    <div>
        <section v-for="ambiente in allambientes.data" :key="ambiente.id">
            <h1>Ambientes: </h1> 
            <h3>{{ ambiente.nome }}</h3>
        </section>
        <div>
            <label for="">Qtd. Ambiente:</label> <input type="text" v-model="ambientePost"> <br>
        </div>
        <button @click="saveAmbiente">Adicionar Ambiente</button>
    </div>
    
</template>