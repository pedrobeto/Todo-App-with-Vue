<template>
    <div class="todo-item" >
            <div class="nameChecked">
                <input type="checkbox" v-on:change="changeComplete">
                {{ todo.title }}
                <span class="done-pin" v-bind:class="{'is-complete':todo.completed}">
                DONE
                </span>
            </div>
            
            <button @click="$emit('del-todo', todo.id)" class="del">x</button>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        changeComplete() {
            this.$emit('completeToggle', this.todo.id);
        }
    }
}
</script>

<style scope>
    .todo-item {
    background: #dadada;
    padding: 10px;
    height: -webkit-fit-content;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    padding: 10px 12px;
    font-weight: 400;
  }
  .is-complete {
    visibility: visible !important;
  }
  .del {
    background: #D30000;
    color: #fff;
    border: none;
    border-radius: 50%;
    cursor: pointer;
    float: right;
    height: 20px;
    width: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 12px;
    font-size: 1rem;
    justify-self: flex-end;
  }

  .nameChecked {
      flex: 1;
  }
  input[type="checkbox"] {
      margin: 6px;
  }

  .done-pin {
      height: 8px;
      width: 15px;
      background: #00e600;
      font-size: 0.76rem;
      padding: 2px 8px;
      margin-left: 4px;
      border-radius: 6px;
      visibility: hidden;
  }

  

</style>