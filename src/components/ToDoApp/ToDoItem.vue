<template>
    <div class="todoRow">
        <div class="todoRow-inner">
            <input type="checkbox" v-model="item.compleated" />
            <label :class="{ compleated: item.compleated }">{{ item.text }}</label>
        </div>
    </div>
</template>
<script>
    export default {
        props: {
            item: Object
        }
    };
</script>
<style scoped>
    .compleated{text-decoration:line-through;}
    .todoRow{float:left;width:100%;border-bottom:1px solid #ddd;padding:10px;font-size:14px;color:#fff;display:flex;align-items:center;gap:10px;height:50px;}
    .todoRow-inner{float:left;position:relative;}
    .todoRow-inner input{position:absolute;left:0;right:0;top:0;bottom:0;width:100%;opacity:0;}
    .todoRow-inner label:before{content:'';float:left;width:20px;height:20px;border:1px solid;border-radius:50%;}
    .todoRow-inner label{display:flex;align-items:center;gap:10px;}
    .todoRow-inner label.compleated:before{background:#fff;}
</style>