<template>
<div class="todoListContainer">
    <div class="heading">
        <h2 id="title">
            ToDo List
        </h2>
        <addItemForm
            v-on:reloadList="getList"
        ></addItemForm>
        <listView :items="items"
                  v-on:reloadList="getList"
        ></listView>
    </div>


</div>
</template>

<script>
import addItemForm from "./addItemForm";
import listView from "./listView";
export default {
    components: {
        addItemForm,
        listView,
    },
    data: function() {
        return {
            items:[],
        }
    },
    methods: {
        getList() {
            axios.get('api/items')
            .then(response => {
               this.items = response.data
            })
            .catch(error => {
                console.log(error)
            })
        }
    },
    created() {
        this.getList()
    }
}
</script>

<style scoped>
.todoListContainer {
    width: 400px;
    margin: auto;
}
.heading {
    background: #718096;
    padding: 10px;
}
#title {
    text-align: center;
}
</style>
