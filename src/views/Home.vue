<template>
    <div>
        <h2>Home page</h2>
        <h3>Click Todos!</h3>
        <router-link to="/todos" class="linka">Todos</router-link>
    </div>
</template>
<style scoped>
    div {
        height: 140px;
    }
    h3{
        color: teal;
    }
    .linka{
        color: tomato;
        text-decoration: none;
        font-weight: 600;
        font-size: 18px;
        border: orangered 1px solid;
        border-radius: 3px;
        padding: 5px;
        margin-bottom: 20px;
        cursor: pointer;
    }
</style>