<template>
    <div>
        <input type="text" v-model="addItemText" @keyup.enter="add()">
        <button type="submit" @click.prevent="add">할 일 추가</button><br>
        <item-list val='addItemTitle' ref='child'></item-list>
        <!-- <item-list
            v-for="(item,index) in items"
            :key="index"
            v-bind:todo="item.todo"
            :checked="item.checked"
            v-on:remove="items.splice(index, 1)">
        </item-list> -->
    </div>
</template>

<script>
import ItemList from './ItemList'

export default {
    name: 'add-item',
    components: {
        'item-list': ItemList
    },
    data() {
        return {
            addItemText: '',
            // items:[{todo: 'TodoList 할 일 추가', checked: true}]
        }
    }, 
    methods:{
        add() {
            if (this.addItemText=='') {
                alert("내용을 입력하세요")
                return
            }
            this.$refs.child.addItem(this.addItemText.trim())
            this.addItemText = ''
        }
    }
}

</script>
