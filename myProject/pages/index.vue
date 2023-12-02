<script setup>

    definePageMeta({
        layout: "layout-login"
    })

    const {data: allusers} = await useFetch('http://127.0.0.1:8000/usuarios');
</script>


<template>
    <div>
        <div>
            <h1>Seja bem vindo!</h1>
            <br><br>
            <h2>Login</h2>
        </div>
        
        <div>
            <label for="">Email: </label>
            <select @click="emailSelect">
                <option v-for="user in allusers.data"
                :key="user.id" :value="user.email">{{ user.email }}</option>
            </select>
            <br>
            <NuxtLink :to="`/menu`">
                <button>Buscar</button>
            </NuxtLink>
        </div>
    </div>
</template>