<template>
  <h1>Hello World!</h1>
  
  <!-- <Modal></Modal> -->
  <div v-if="showModal">
  
    <Modal :header="header" :content="content" :theme="theme" @close="showModal=false">

      <h3>Simple Slot</h3>
      <template v-slot:namedSlot>
        <h4>Named Slot</h4>
      </template>
    </Modal>

  </div> 

  <teleport to=".teleport-part">
    <h1>Teleport Part</h1>
  </teleport>
  <button @click="showModal=true">show modal</button>

  <!-- delete Modal Start-->
  <div v-if="delModal" >

    <Modal :delHeader="delHeader" :delContent="delContent" theme="delete" @close="delModal=false"/>

  </div> 
  <button @click="delModal=true">delete modal</button>

  
</template>

<script>
import Modal from "./components/Modal-modal.vue"

export default {
  data(){
    return{
      header: "Login Success",
      content: "Hello World!",
      theme: "success",
      showModal: false,
      delModal: false,
      delHeader: "Delete Modal",
      delContent: "Are you sure to delete?"
      
    }
  },
  components:{
    // Modal : Modal
    Modal,
    
  }
}
</script>

<style scoped>
  h1{
    color: aquamarine;
  }
</style>