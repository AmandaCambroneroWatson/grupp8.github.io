<template>
  <div>
    <form id="overlay">
      <input
        placeholder="Task name"
        type="text"
        name=""
        id="OverlayInput"
        v-model="title"
      />
      <PreviewColor :title="title" :color="color" />
      <h3>Pick a color</h3>
      <div id="colorPicker">
        <input type="color" v-model="color" />
      </div>
      <button
        :disabled="title.length == 0"
        @click="addTask()"
        class="addtaskbutton"
        id="save"
      >
        Add Task
      </button>
      <p id="close" @click="closeOverlay">Cancel</p>
    </form>
  </div>
</template>
<script>
  import PreviewColor from '@/components/PreviewColor.vue'
  export default {
    name: 'AddTask',
    components: {
      PreviewColor
    },
    data() {
      return {
        title: '',
        color: '#ffa500'
      }
    },
    methods: {
      addTask() {
        this.$store.commit('addTask', {
          title: this.title,
          listId: this.listId,
          color: this.color // Change to dynamic color picker value
        })
        this.closeOverlay()
      },
      closeOverlay() {
        this.$emit('closeOverlay')
      }
    },
    props: {
      listId: String
    }
  }
</script>
<style scoped>
  #overlay {
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: #ffff;
    position: fixed;
    width: 380px;
    height: 525px;
    top: 50%;
    left: 50%;
    margin-top: -50px;
    transform: translate(-50%, -50%);
    border-radius: 3%;
    box-shadow: 0px 0px 100px 2000px rgba(0, 0, 0, 0.5);
  }

  input[type='color'] {
    border: 0;
    padding: 0;
    width: 200%;
    height: 200%;
    cursor: pointer;
    transform: translate(-25%, -25%);
  }

  #colorPicker {
    width: 50px;
    height: 50px;
    margin-bottom: 50px;
    border-radius: 50px;
    overflow: hidden;
    border: 2px solid grey;
  }

  #OverlayInput {
    margin-top: 45px;
    margin-bottom: 10px;
    width: 343px;
  }

  .addtaskbutton {
    width: 350px;
    margin: 8px 0;
    background-color: #5db075;
    padding: 16px 32px;
    border-radius: 25px;
    border: none;
    cursor: pointer;
    color: #fff;
    font-style: normal;
    font-weight: 600;
    font-size: 14px;
  }
</style>
