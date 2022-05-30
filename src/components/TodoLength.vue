<script setup>
defineProps(["todo", "filter", "filters"]);
</script>

<template>
<div class="span-list">
    <span v-show="todo">{{ todo }} Adet Todo Var.</span>
    <div class="active" v-show="filter.length > 0">
        {{ filter.length }} Adet Tamamlanmış Todo Var.
    </div>
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
        padding: 5px 30px;
        border-radius: 5px;
        color: white;
        background: #ffaa46;
    }
}

.active {
    background: rgb(114, 199, 102);
    display: flex;
    justify-content: flex-start;
    padding: 5px 30px;
    border-radius: 5px;
    color: white;
}
</style>
