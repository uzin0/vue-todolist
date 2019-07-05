<template>
    <div>
        <banner-component/>
        <add-item/>
    </div>
</template>

<script>
import Banner from './Banner'
import AddItem from './AddItem'

export default {
    name: 'screen-component',
    components: {
        'banner-component': Banner,
        'add-item': AddItem
    }
} 
</script>
<style scoped>
#item{
    width: 300px;
    height: 50px;
    margin: auto;
    border-bottom: 2px solid gray;
}

#item div{
    display: inline;
}
</style>