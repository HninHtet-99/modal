<template>
  <div class="backdrop" @click.self="hideModal">

    <div class="modal" :class="{green : theme ==='success', red : theme === 'delete'}">
        <div v-if="theme === 'success'">

            <h1 >{{header}}</h1>
            <p>{{content}}</p>
            <!-- <slot/> -->
            <slot>
                default slot
            </slot>
            <slot name="namedSlot"/>

        </div>
        
        <div v-else>
            <h1>{{delHeader}}</h1>
            <p>{{delContent}}</p>
        </div>
        
    </div>

  </div>
</template>

<script>
export default {
    props:["header","content","theme",'delHeader',"delContent"],
    methods:{
        hideModal(){
            this.$emit("close"); 
        }
    }
}
</script>

<style scoped>
    .backdrop{
        position: fixed;
        top: 0;
        background: rgb(0, 0, 0, 0.5);
        width: 100%;
        height: 100vh;
    }
    .modal{
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background-color: #f5f5f5;
        border-radius: 10px;
    }
    p{
        font-style: normal;
    }
    .green{
        background-color: green;
        color: white;
    }
    .red{
        background-color: red;
        color: white;
    }
</style>