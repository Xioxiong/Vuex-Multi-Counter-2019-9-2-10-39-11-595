<template>
    <ul class="items">
        <template v-for="(item,index) in filteredTodoList">
            <li :key="index" :class="item.status">
                <input name="status-toggle" :checked="item.status === 'completed'" type="checkbox"
                       @change="handleToggleActive(index)">
                <label href="" @click="update(item.id)"  :class="content">{{item.content}}</label>
            </li>
        </template>
    </ul>
</template>

<script>
    import {mapState, mapMutations} from "vuex";

    export default {
        name: "todo",
        computed: {
            filteredTodoList: function () {
                return this.$store.getters.filteredTodoList;
            }
        },
        methods: {
            handleToggleActive: function (index) {
                 this.$store.commit("changeStatus", index);
            },
            update:function(id){
                this.$store.dispatch('updateTodos',id);
            }
        }
    }
</script>

<style scoped>

</style>
