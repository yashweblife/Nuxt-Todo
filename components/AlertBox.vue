<template>
    <div class="alert-box" :class="(alert_open || trigger) ? '' : 'close'">
        <div>
            <h1>Add a List</h1>
            <input type="text" v-for="input in inputs" :key="input.id" v-model="input.name" :placeholder="input.placeholder">
            <nav>
                <button @click="completeData">Confirm</button><button @click="()=>{completeData(0)}">Discard</button>
            </nav>
        </div>
    </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
    name:"AlertBox",
    data: () => {
        return ({
            alert_open: false
        })
    },
    props:["title", "inputs", "trigger"],
    methods:{
        closeAlertBox(){
            this.alert_open = false
        },
        completeData(a:any){
            if(a===0){
                this.$emit("alert-box-completed", [])
            }else{
                var data = this.inputs.map((i:any)=>i.name)
                this.$emit("alert-box-completed", data)
                this.closeAlertBox()

            }
        }
    }
})
</script>

<style lang="scss" scoped>
.alert-box {
    width: 100vw;
    height: 100vh;
    position: absolute;
    top: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;

    &.close {
        display:none !important;
    }

    >div {
        width: 300px;
        padding: 1em;
        border-radius: 1em;
        box-shadow: 0 0 1em 0em rgba(0, 0, 0, 0.3);
        background-color: rgb(29, 29, 29);
        color: white;

        >h1 {
            text-align: right;
        }

        input {
            font-size: 1.3em;
            width: 100%;
            background-color: transparent;
            color: white;
            border: 0;
            border-bottom: 0.1em solid white;
        }

        nav {
            width: 100%;
            display: flex;
            align-items: center;
            margin: 1em 0;

            >button {
                width: 100%;
                margin: 0.2em;
            }
        }
    }
}
</style>