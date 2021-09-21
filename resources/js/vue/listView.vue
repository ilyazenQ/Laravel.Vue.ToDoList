<template>
<div>
    <div v-for="(item,i) in items" :key="i">

        <listItem
        :item="item"
        class="item"
        v-on:itemChanged="$emit('reloadList')"
        >

        </listItem>

    </div>
</div>
</template>

<script>
import listItem from "./listItem";

export default {
    props:['items'],
    components: {
        listItem
    }

}
</script>

<style scoped>
.item {
    background: #cbd5e0;
    padding:5px;
    margin-top:10px;
}
</style>
