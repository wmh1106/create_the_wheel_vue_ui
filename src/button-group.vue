<template>
    <div class="g-button-group">
        <slot></slot>
    </div>
</template>
<script>
export default {
    name:'ButtonGroup'
}
</script>
<style lang="scss" scoped>
.g-button-group{
    display:inline-flex;
    vertical-align: middle;
    > .g-button{
        position: relative;
        z-index: 0;
        border-radius:0;
        &:not(:first-of-type){
            margin-left:-1px;
        }
        &:first-child{
            border-top-left-radius: var(--border-radius);
            border-bottom-left-radius: var(--border-radius);
        }
        &:last-child{

            border-top-right-radius: var(--border-radius);
            border-bottom-right-radius: var(--border-radius);
        }
        &:hover{
            z-index: 1;
        }
    }
}
</style>

