<template>
    <div class="todoNew">
        <input type="text" v-model="newToDo" @keyup.enter="addToDo" placeholder="Create a new todo...">
    </div>
</template>
<script>
    export default{
        data(){
            return{
                newToDo: ''
            }
        },
        methods:{
            addToDo(){
                this.$emit('add',this.newToDo);
                this.newToDo = '';
            }
        }
    }
</script>
<style scoped>
    .todoNew{float:left;width:100%;background:#333;padding:10px;height:50px;display:flex;align-items:center;gap:10px;margin-bottom:10px;}
    .todoNew input{border:0;background:no-repeat;width:100%;outline:0;color:#fff;}
</style>