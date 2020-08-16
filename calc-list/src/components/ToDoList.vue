<template>
<div class="todo-list">
    <input type="text" name="inputbox" v-model="item" placeholder="Enter item to be added"/>
    <button @click="addToList()">Add</button>
    <li v-for="item in listItem" :key="item.id">
        {{item.name}}
        <button @click="removeFromList(item.id)">x</button> 
    </li>
</div>        
</template>

<script>
export default {
    name: 'ToDoList',
    data: function() {
        return {
            listItem : [
            {
                id: 1,
                name: 'milk',
            },
            {
                id: 2,
                name: 'bread',
            },
            {
                id: 3,
                name: 'oats',
            }
        ],
        item: "",
        }
    },
    methods: {
        addToList() {
            var newItemId = this.listItem.length + 1;
            var newItem = {id: newItemId, name: this.item};
            this.listItem.push(newItem);
        },
        removeFromList(index) {
            this.listItem.splice(index-1, 1);
        },
    }
}
</script>