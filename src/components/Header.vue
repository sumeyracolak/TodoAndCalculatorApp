<template>
    <header>
        <RouterLink to="/">Todo App</RouterLink>
        <RouterLink to="/calculator">Calculator App</RouterLink>
      </header>
</template>
<style scoped lang="scss">
    header{
        position: absolute;
        left: 0;
        top: 0;
        right: 0;
        display: flex;
        padding: 20px;
        gap: 20px;
        a{
            display: block;
            color: #000;
        }.router-link-active {
            background-color: hsla(160, 100%, 37%, 0.2);
        }
    }
</style>