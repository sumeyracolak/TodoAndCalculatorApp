<script setup>
    import DocumentationIcon from '../icons/IconDocumentation.vue'
</script>
<template>
    <div class="toDoBottom">
        <div class="toDoBottom-col">
            <span>{{leftItems}} items left</span>
        </div>
        <div class="toDoBottom-col">
            <span @click="showAllItems">All</span>
            <span @click="showActiveItems">Active</span>
            <span @click="showCompleatedItems">Compleated</span>
        </div>
        <div class="toDoBottom-col">
            <span @click="removeCompleatedItems">Clear Compleated</span>
        </div>
    </div>
</template>
<style scoped>
    .toDoBottom{display:flex;float:left;width:100%;background:#333;color:#fff;padding:10px;height:50px;}
    .toDoBottom-col{display: flex;gap: 10px;width: 33.33%;}
    .toDoBottom-col:last-child{justify-content: flex-end;}
    .toDoBottom-col span{cursor: pointer;}
</style>
<script>
    export default{
        props:{
            leftItems:{
                type: Number
            }
        },
        methods:{
            showAllItems() {
                this.$emit('showAllItems');
            },
            removeCompleatedItems(){
                this.$emit('removeCompleatedItems');
            },
            showCompleatedItems(){
                this.$emit('showCompleatedItems');
            },
            showActiveItems(){
                this.$emit('showActiveItems');
            }
        }
    }
</script>