<script setuo>
defineProps(["todo", "filter", "filters"]);
</script>

<template>
<div class="span-list">
    <span v-show="todo">{{ todo }} Adet Todo Var.</span>
    <span class="active" v-show="filter.length > 0">
        {{ filter.length }} Adet Tamamlanmış Todo Var.
    </span>
    <span v-show="filters.length > 0">{{ filters.length }} Adet Tamamlanmamış Todo Var.</span>
</div>
</template>

<style lang="scss" scoped>
.span-list {
    display: flex;
    justify-content: space-between;
    margin: 0px 35px;

    span {
        display: flex;
        justify-content: flex-start;
        padding: 5px 30px;
        border-radius: 5px;
        color: white;
        background: #f49d3a;
        border: 1px solid black;
        margin-right: 10px;
    }
}
</style>
