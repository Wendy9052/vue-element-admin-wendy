<template>
  <div class="title_box" :title="title">
        {{title}}
  </div>
</template>

<script>
export default {
    name:"topBar",
    props:{
        title:{
            type:String,
            default:"标题"
        }
    }
}
</script>

<style lang="scss" scoped>
.title_box{
    height: 50px;
    background: #ccc;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #000;
    font-size: 17px;
}
</style>