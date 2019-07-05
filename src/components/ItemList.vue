<template>
    <div>
        <div id="item" v-for="(item,index) in items" :key="index">
            <div ><input type="checkbox" id="checkbox" :checked="item.checked" v-model="item.checked" ></div>
            <div id="title" v-on:click="modal_rendar(item,index)" v-bind:style="[item.checked ? styleA:styleB]">{{item.todo}}</div>
            <div id="delete" v-on:click="remove(index)">x</div>
        </div>
        <modals-container v-on:modify="change"></modals-container>
    </div>
</template>

<script>
import Modal from './Modal'
export default {
    name: 'item-list',
    props: ['itemText'],
    data() {
        return{
            items: [{todo:'TodoList 끝내기',checked:true}],
            styleA: {color: 'lightgray', fontStyle: 'italic', textDecoration: 'line-through'},
            styleB: {color: 'black'},
            index: 0
        }
    },
    methods:{
        remove(index) {
            if(confirm( '정말 삭제하시겠습니까?' )) {
                return this.items.splice(index, 1)
            }
        },
        addItem(value){
            this.items.push({todo:value,checked:false});
        },
        modal_rendar(item,index) {
            if(!item.checked){
                this.$modal.show(Modal,
                                {itemText: item.todo, itemIndex: index, modal: this.$modal},
                                {name: 'dynamic-modal', width : '330px',height : '130px', draggable: true,})            
                return
            }
            alert("이미 완료된 항목입니다.")

        },
        change: function(message,index) {
            this.items[index].todo = message
        } 
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