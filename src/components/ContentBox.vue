<template>
  <div id="content-box">
    <div>
      <div class="input_form p-20" >
        <input type="text" placeholder="Enter name.." v-model="name">
        <button type="button" @click="addNameToList">Add Name</button>
      </div>

      <div class="p-20" v-if="list.length > 0">
        <div class="list_box">
          <ul>
            <li class="list_item" :key="item" v-for="(item, index) in list">
              <div >
                <span class="number">{{parseInt(index) + 1}}.</span>  
                <span class="name">
                  &nbsp; {{ item }}
                </span>
              </div>
              <i @click="removeItemFromList(index)">&times;</i>
            </li>
          </ul>
          <div class="draw-box text-center">
            <span>{{ drawCount }}</span>
            <div class="counter_btn">
              <button @click="incrementCounter">+</button>
              <button @click="decrementCounter">-</button>
            </div>
            <button 
              @click="draw"
              class="draw_btn"
            >Draw</button>
          </div>
        </div>
      </div>
      <div class="error pl-20" v-else>
        Enter some names in the list.
      </div>
      <Modal 
        v-show="pickedIndexes.length > 0"
        @close="closeModal"
      >
        <ul class="mt-10">
          <li v-for="item in pickedIndexes" :key="item">{{ item }}</li>
        </ul>
      </Modal>
    </div>
  </div>
</template>

<script>
import Modal from './Modal';
export default {
  data() {
    return {
      name: '',
      list: [
        
      ],
      drawCount: 1,
      pickedIndexes: []
    }
  },
  components: {
    Modal
  },
  methods: {
    removeItemFromList(index) {
      this.list.splice(index, 1);
      this.pickedIndexes = [];
      this.drawCount = 1;
    },
    closeModal() {
      this.pickedIndexes = [];
    },
    addNameToList() {
      if(this.name.trim() !== '') {
        this.list.push(this.name);
        this.name = '';
      }
    },
    incrementCounter() {
      if(this.drawCount < this.list.length-1) {
        this.drawCount++;
      }
    },
    decrementCounter() {
      if(this.drawCount > 1) {
        this.drawCount--;
      } 
    },
    getRandomIndex(min, max) {
      return Math.random() * (max - min + 1);
    },
    draw() {
      this.pickedIndexes = [];
      if(this.drawCount == this.list.length) {
        this.pickedIndexes = this.list;
      } else {
        for(let i=0; i<this.drawCount; i++) {
          
          let index = Math.floor(this.getRandomIndex(0, this.list.length - 1));
          let pickedItem = this.list[index];
          if(!this.pickedIndexes.includes(pickedItem)) {
            this.pickedIndexes.push(pickedItem);
          } else {
            i--; // keep the i same to keep the loop running.
          }
          
        }
      }
    }
  }
}
</script>

<style scoped>
  .list_item {
    display: flex;
    justify-content: space-between;
    margin-right: 20px;
  }
  .list_item i {
    font-size: 30px;
  }
  .mt-10 {
    margin-top: 10px;
  }
  .list_box {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .list_box div {
    flex: 1;
  }
  .text-center {
    text-align: center;
  }
  .error {
    color: yellow;
    font-size: 18px;
    padding-top: 10px;
    letter-spacing: 1px;
  }

  .input_form {
    display: flex;
  }

  .input_form button {
    font-size: 16px;
    flex: 2;
  }

  #content-box {
    min-height: 80vh;
    overflow:auto;
    display:flex;
    align-items: center;
    justify-content: center;
    position:relative;
    animation-name: content_app_animation;
    animation-duration: 2s;
  }

  @keyframes content_app_animation {
    0% {
      display:none;
      opacity: 0;
    }

    100% {
      opacity: 1;
    }
  }

  .p-20 {
    padding: 20px;
  }
  .pl-20 {
    padding-left: 20px;
  }

  ul {
    list-style-type: none;
    flex: 3;
  }

  ul li .number{
    font-size: 22px;
    color: #da0a77;
    font-weight: bolder;
  }
  ul li .name{
    font-size: 26px;
    color: #eea42e;
    font-weight: bolder;
  }

  input {
    font-size: 22px;
    padding: 10px;
    width: 100%;
    font-family: inherit;
    display: block;
    box-sizing: border-box;
    flex: 3;
    font-weight: bold;
  }
  button {
    font-size: 22px;
    background: rgb(112, 5, 112);
    color: white;
    border: none;
    border-top-right-radius: 8px;
    border-bottom-right-radius: 8px;
    cursor: pointer;
    transition: background 0.3s;
  }

  button:hover {
    background: rgb(71, 3, 71);;
  }

  .draw_btn {
    border-radius: 0px;
    width: 100%;
    padding: 20px;
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
    
  }
  .counter_btn {
    display:flex;
  }

  .counter_btn button {
    border-radius: 0px;
    padding: 10px 20px;
    flex: 1;
    border: 1px solid maroon;
    font-size: 42px;
  }

  .draw-box span{
    border-top: 3px solid purple;
    border-left: 3px solid purple;
    border-right: 3px solid purple;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 48px;
    font-weight: bold;
    height: 100px;
  }

  #content-box > div {
    width: 80%;
  }
  
  

  @media screen and (max-width: 600px) {
    .input_form button {
      flex: 2;
    }

    #content-box > div{
      width: 100%;
      box-sizing: border-box;
    }
    .list_box {
      display: block;
    }
    .draw-box {
      margin-top: 30px;
    }
  }
</style>