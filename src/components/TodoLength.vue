<script setup>
defineProps(["todo", "filter", "filters"]);
</script>

<template>
<div class="span-list">
    <span v-show="todo">{{ todo }} Adet Todo Var.</span>
    <span v-show="filter.length > 0">{{ filter.length }} Adet Tamamlanmış Todo Var.</span>
    <span v-show="filters.length > 0">{{ filters.length }} Adet Tamamlanmamış Todo Var.</span>
</div>
</template>

<style lang="scss" scoped>
.span-list {
    display: flex;
    justify-content: space-between;

    span {
        display: flex;
        justify-content: flex-start;
        border: 1px solid black;
        background: rgb(255, 170, 70);
        padding: 5px 30px;
        border-radius: 5px;
    }
}
</style>
