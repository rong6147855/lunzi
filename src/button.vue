<template>
    <button calss="g-button">按钮</button>
</template>
<script>
export default {}
</script>
<style lang="scss">
  .g-button{
            font-size: var(--font-size);
            height:var(--button-height);
            padding: 0 1em;
            border-radius: var(--border-radius);
            border: 1px solid var(--border-color);
            background: var(--button-bg);
        &:hover{
            border-color:var(--border-color-hover);
        }//&表示当前选择器
        &:active{
            background-color: var(--button-active-bg);
        }
        &:focus{
            outline: none;
        }
  }

</style>