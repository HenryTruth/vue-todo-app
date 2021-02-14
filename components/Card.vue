<template>
    <section>
        <div class="card">
            <slot name='content'/>
        </div>
    </section>
</template>

<script>
export default {
    
}
</script>

<style lang="less" scoped>

.card{
    background-color: white;
    margin: 3rem;
    height: 10rem;
    box-shadow: 2px 2px 11px #000000;
    border-radius: 3px;
    padding: 1rem;
    
}
    

</style>