<template>
  <div class="addItem">
      <input type="text" v-model="item.name">
      <button
          @click="addItem()"
      :class="[item.name ? 'active': 'inactive']"
      >Добавить</button>
  </div>
</template>

<script>
export default {
    data: function () {
        return{
            item:{
                name:""
            }
        }
    },
    methods:{
        addItem(){
            if(!this.item.name){
                return;
            }
            axios.post('api/item/store', {
                item:this.item,
            })
                .then(response=> {
                if(response.status == 201){
                    this.item.name = "";
                    this.$emit('reloadList');
                }
            })
                .catch(error => {
                console.log(error);
            })
        }
    }
}
</script>

<style scoped>
.addItem {
    display: flex;
    justify-content: center;
    align-items: center;
}
.active {
    background: green;
    padding:8px;
    color:white;
}
.inactive{
    background: white;
    padding:2px;
}

</style>
