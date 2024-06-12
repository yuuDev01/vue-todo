<template>
    <div class="clearAllContainer">
        <span class="clearAllBtn" @click="clearTodo">전체 삭제</span>
    </div>
</template>

<script>
export default{
    methods:{
        clearTodo(){
            this.$emit('removeAll');
        }
    }

}
</script>

<style scoped>
    .clearAllContainer{
        width: 8.5rem;
        height: 50px;
        line-height: 50px;
        background-color: white;
        border-radius: 5px;
        margin: 0 auto;;
        cursor : pointer;
    }

    .clearAllContainer:active{
        background: rgb(175, 175, 175);
    }


    .clearAllBtn{
        color: #e20303;
        display: black;
    }
</style>