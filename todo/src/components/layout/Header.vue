<template>
    <header class="header">
        <div id="title">
            <h1>Todo List with  </h1>
            <span><img id="logoImg" src="../../../public/icon-logo.svg" alt=""></span>
        </div>
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
    #title {
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 0.9rem;
    }
    #logoImg {
        width: 32px;
        height: 32px;
    }
</style>