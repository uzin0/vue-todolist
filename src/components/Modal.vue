<template>
    <div class="container">
        <div>
            <span>
                할 일 :
            </span>
            <input type="text" v-model="text"  @keyup.enter="ok()">
        </div>
        <div> 
            <input @click="ok" type="button" value="수정">
            <input @click="close" type="button" value="취소">
        </div>
    </div>
</template>
<script>
export default {
    name: 'modal-component',
    props: ['itemText','itemIndex'],
    data() {
        return {
            text: this.itemText
        }
    },
    methods : {
        ok() {
            this.$emit('modify',this.text,this.itemIndex)
            this.$emit('close')
        },
        close() {
            this.$emit('close')
        }
    }
}
</script>
