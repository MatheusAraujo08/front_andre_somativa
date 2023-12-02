<script setup>

    const {data: allcargos} = await useFetch('http://localhost:8000/cargos?all');
    
</script>

<template>
    <div>
        <section v-for="cargo in allcargos.data" :key="cargo.id">
            <h1>Cargos: </h1> 
            <h3>{{ cargo.nome }}</h3>
            <h1>Nivel de acesso: </h1>
            <h3>{{  cargo.nivelAcesso }}</h3>
        </section>
    </div>
</template>