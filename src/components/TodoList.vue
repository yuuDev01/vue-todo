<template>
    <section>
        <transition-group name="list" tag="ul">
            <li v-for="(todoItem,index) in propsdata" :key="todoItem" class="shadow">
                <i class="checkBtn fas fa-check" aria-hidden="true"></i>
                {{ todoItem }}
                <span class="reviseBtn" type="button" @click="reviseTodo(todoItem, index)">수정</span>
                <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li>
        </transition-group>
    </section>
</template>

<script>
import eventBus from './common/eventBus'
export default{
    props:['propsdata'],
    methods:{
        removeTodo(todoItem, index){
            //삭제 이벤트 발생, 상위컴포넌트로 전달
            this.$emit('removeTodo', todoItem, index);
        },
        reviseTodo(todoItem, index){
            //수정 이벤트 발생, todoinput 컴포넌트로 해당 아이템 전달
            eventBus.$emit('reviseTodo', todoItem, index);
        }
    }

}
</script>

<style scope>
    ul{
        list-style-type: none;
        padding-left: 0px;
        margin-top:0;
        text-align: left;
    }
    li{
        display : flex ;
        min-height: 50px;
        height: 50px;
        line-height:50px;
        margin:0.5rem 0;
        padding: 0 0.9rem;
        background: white;
        border-radius: 5px;
    }
    
    .checkBtn{
        line-height: 45px;
        color: #62acde;
        margin-right: 5px;
    }

    .removeBtn{
        margin-left: 20px;
        color: #de4343;
    }

    .list-enter-active, .list-leave-active{
        transition: all 1s;
    }

    .list-enter, .list-leave-to{
        opacity: 0;
        transform: translateY(30px);
    }

    .reviseBtn{
        margin-left:auto;
        background-color : yellow
    }
</style>