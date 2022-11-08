<template>
    <section>
        
        <ul>
            <ItemVue v-for="item in list" :key="item.id" :item="item" @item-deleted="deleteItem" />
        </ul>
        <nav>
            <input type="text" v-model="newItemInput">
            <textarea name="info" cols="30" rows="10" v-model="newItemInfoInput"></textarea>
            <button @click="addNewItem">Add</button>
        </nav>
    </section>
</template>
<script lang="ts">
import Vue from 'vue'
import ItemVue from '~/components/Item.vue';
import { ItemInterface } from '~/interfaces';


export default Vue.extend({
    data: () => {
        const list: ItemInterface[] = [
            {
                title: "A",
                info: "Hello World",
                id: 0,
                marked: false
            },
            {
                title: "B",
                info: "Hello World",
                id: 1,
                marked: false
            },
            {
                title: "C",
                info: "Hello World",
                id: 2,
                marked: false
            },
        ]
        return ({
            list,
            newItemInput: "",
            newItemInfoInput: ""
        })
    },
    components: {
        ItemVue
    },
    methods: {
        deleteItem(value: number) {
            console.log("HELLO WORLD")
            var nList: ItemInterface[] = []
            this.list.forEach((item: ItemInterface) => {
                if (item.id != value) {
                    nList.push(item)
                }
            })
            this.list = nList
        },
        addNewItem() {
            this.list.push({
                title: this.newItemInput,
                info: this.newItemInfoInput,
                id: Math.random(),
                marked: false
            })
            this.newItemInfoInput = ""
            this.newItemInput = ""
        }
    }
})
</script>
<style lang="scss" scoped>
section {
    font-family: Arial, Helvetica, sans-serif;
    padding: 1em;
    display: flex;
    flex-direction: column;
    align-items: center;
    ul{
        width:500px;
        height: 500px;
        overflow-y: auto;
        padding: 1em;
        box-shadow: inset 0 -1em 1em -1em rgba(0,0,0,0.1), 0 0 1em 0 rgba(0,0,0,0.5);
        border-radius: 1em;
        &::-webkit-scrollbar{
            width:0.5em;
        }
        &::-webkit-scrollbar-thumb{
            background-color: rgb(26, 187, 171);
            border-radius: 1em;
        }
    }
    >nav{
        width:300px;
        display: flex;
        flex-direction: column;
        align-items: center;
        input,textarea{
            width:100%;
            font-size: 1.2em;
            border-bottom: 0.2em solid rgb(26, 187, 171);
            border:0.1em solid rgba(0,0,0,0.1);
        }
        input{
            font-size: 1.5em;
        }
        button{
                width: 100%;
                margin:0.5em;
                border:0;
                outline:none;
                cursor:pointer;
                background-color: rgb(26, 187, 171);
                padding: 0.5em;
                border-radius: 1em;
                font-size: 1em;
            }
    }
}
</style>