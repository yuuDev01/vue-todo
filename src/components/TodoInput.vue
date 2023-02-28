<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo">
        <!-- 추가버튼 -->
        <span class="addContainer" v-on:click="addTodo">
            
            <i class="addBtn fas fa-plus" aria-hidden="true"></i>
        </span>
    </div>
</template>

<script>
export default{
    data(){
        return{
            newTodoItem:''
        }
    },
    methods:{
        addTodo(){
            if(this.newTodoItem !=""){
                var value = this.newTodoItem && this.newTodoItem.trim() //공백제거
                this.$emit("addTodo", value); //이벤트이름, value값 전달
                this.clearInput();
            }
        },
        clearInput(){
            this.newTodoItem='';
        }
    }

}
</script>

<style>
input:focus{
    outline: none;
}
.inputBox{
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
}
.inputBox input{
    border-style: none;
    font-size: 0.9rem;
}
.addContainer{
    float: right;
    background: linear-gradient(to right, #6478FB, #8763FB);
    /* display: block; */
    width: 3rem;
    border-radius: 0 5px 5px 0;
}
.addBtn{
    color: white;
    vertical-align: middle;
}
</style>