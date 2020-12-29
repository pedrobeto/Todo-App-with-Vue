<template>
    <header class="header">
        <h1>Todo List</h1>
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/">About</router-link>
        </div>
    </header>
</template>

<script>
import icon from '../../../public/icon-logo.svg';

export default {
    name: 'Header',
    data() {
        return {
            icon: icon
        }
    }
}
</script>

<style scoped>
    .header {
        background: #333;
        color: #fff;
        text-align: center;
        padding: 10px;
    }
    #nav a {
        color: #fafafa;
        padding-right: 5px;
        text-decoration: none;
    }
</style>