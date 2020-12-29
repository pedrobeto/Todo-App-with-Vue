<template>
    <div class="wrap-container">
        <form @submit="addTodo" class="add-form">
            <input type="text" v-model="title" name="title" placeholder="Add todo here...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>

export default {
    name: 'AddTodo',
    data() {
        return {
            title: '',
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            if (this.title != '') {
                const newTodo = {
                title: this.title,
                completed: false,
            }

            // send up to parent
            this.$emit('add-todo', newTodo);

            this.title='';
            }
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }
    input[type="text"] {
        padding: 10px 12px;
        outline: none;
        font-size: 1.2rem;
        border: none;
        background: #fafafa;
        border-radius: 10px;
        color: #333;
    }
    input[type="submit"] {
        outline: none;
        font-size: 0.92rem;
        margin-left: 12px;
        padding: 0px 12px;
        width: 120px;
        border: none;
        border-radius: 10px;
        cursor: pointer;
        background: #55bed7;
        text-transform: uppercase;
        font-weight: 600;
        color: #fafafa;
    }

    .wrap-container {
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 20px;
    }

    @media only screen and (max-width: 600px) {
        .add-form {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        input[type="submit"] {
            margin: 8px;
            padding: 8px 12px;
        }

        input[type="text"] {
            max-width: 80%;
        }
    }
</style>