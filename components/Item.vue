<template>
    <li :class="marked?'mark':''">
        <h2>{{item.title}}</h2>
        <p>{{item.info}}</p>
        <nav>
            <button @click="test">Mark</button>
            <button @click="$emit('item-deleted',item.id)">Delete</button>
        </nav>
    </li>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    data:()=>{
        return({
            marked:false
        })
    },
    props:['item'],
    methods:{
        test(){
            console.log(1)
            this.marked = !this.marked
        },

    },
})
</script>

<style lang="scss" scoped>
    li{
        list-style-type: none;
        border-left: 0.2em solid rgb(26, 187, 171);
        padding:1em;
        box-shadow: 0 0 1em 0 rgba(0,0,0,0.5);
        border-radius: 1em;
        display:flex;
        align-items: center;
        justify-content: space-between;
        margin:2em 0;
        h2{
            width:200px;
            text-overflow: ellipsis;
            overflow: hidden;
            white-space: nowrap;
        }
        p{
            width:200px;
            text-overflow: ellipsis;
            overflow: hidden;
            white-space: nowrap;
        }
        nav{
            width:200px;
            display: flex;
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
    .mark{
        opacity: 0.3;
        >h2{
            text-decoration: line-through;
        }
    }
</style>