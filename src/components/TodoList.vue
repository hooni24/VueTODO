<template>
    <section>
        <transition-group name="list" tag="ul">
            <li v-bind:key="todoItem" v-for="(todoItem, index) in propsdata" class="shadow">
                <i class="checkBtn fa fa-check" aria-hidden="true"></i>
                {{ todoItem }}
                <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
                    <i class="fa fa-trash-o" aria-hidden="true"></i>
                </span>
            </li>
        </transition-group>
    </section>
</template>


<script>
export default {
    props: ['propsdata'],   // 부모인 App.vue 컴포넌트에서 전달된 props
    methods: {
        removeTodo(item, index) {
            this.$emit("removeTodo", item, index)
        }  
    }
}
</script>

<style>
    ul {
        list-style-type: none;
        padding-left: 0px;
        margin-top: 0px;
        text-align: left;
    }
    li {
        display: flex;
        min-height: 50px;
        height: 50px;
        line-height: 50px;
        margin: 0.5rem 0;
        padding: 0 0.9rem;
        background: white;
        border-radius: 5px;
    }
    .checkBtn {
        line-height: 45px;
        color: #62ACDE;
        margin-right: 5px;
    }
    .removeBtn {
        margin-left: auto;
        color: #DE4343;
    }

    .list-item {
        display: inline-block;
        margin-right: 10px;
    }
    .list-move {
        transition: transform 1s;
    }
    .list-enter-active, .list-leave-active {
        transition: all 1s;
    }
    .list-enter, .list-leave {
        opacity: 0;
        transform: translateY(30px);
    }
</style>
