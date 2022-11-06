<template>
  <div id="demo">
    <drag-selector
      v-model="checkedList"
      class="drag-selector"
      @change="handleDragSelectorChange"
    >
      <drag-selector-item
        v-for="(item, index) in myDragList"
        :key="index"
        :value="item"
        class="drag-selector__item"
      >
       <div @click="handleClick($event, item.name)" style="width: 100%;height: 100%"> {{ item.name }}</div>
      </drag-selector-item>
    </drag-selector>
    <div class="result">
      <div>[<span v-show="!checkedList.length">]</span></div>
      <div v-for="(item,index) in checkedList" :key="`result${index}`">
        &nbsp;&nbsp;&nbsp;&nbsp;{{ item }},
      </div>
      <div v-show="checkedList.length">]</div>
    </div>
    <div class="back">
      <a href="https://github.com/xubaifuCode/vue-drag-selector">Go Back</a>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Demo',
  data() {
    return {
      checkedList: [],
      myDragList: [
        { name: 'item1' },
        { name: 'item2' },
        { name: 'item3' },
        { name: 'item4' },
        { name: 'item5' },
        { name: 'item6' },
        { name: 'item7' },
        { name: 'item8' },
        { name: 'item9' },
        { name: 'item10' },
        { name: 'item11' },
        { name: 'item12' }
      ]
    }
  },
  methods: {
    handleDragSelectorChange(list) {
      console.log('list', list)
    },
    handleClick(e, name) {
      const classList = Array.from(e.target.parentNode.classList)
      if (classList.includes('selected')) {
        e.target.parentNode.classList.remove('selected')
        this.checkedList = this.checkedList.filter(item => {
          return item.name !== name
        })
      } else {
        e.target.parentNode.classList.add('selected')
        this.checkedList.push({ name: name })
      }
    }
  }
}
</script>
<style scoped lang="scss">
body {
  background-color: rgb(250, 250, 250);
}

  #demo {
    width: 740px;
    height: 300px;
    margin-left: auto;
    margin-right: auto;
    background: #B3E5FC;
    border-radius: 4px;
}

  .drag-selector {
    display: flex;
    align-content: flex-start;
    flex-wrap: wrap;
    padding: 10px;
    margin-top: 20px;
}

  .drag-selector__item {
    width: 100px;
    height: 100px;
    margin: 10px;
    border-radius: 4px;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #03A9F4;
    color: white;
}

  .drag-selector__item.selected {
    background-color: #FF4081;
}

  .result {
    background: rgb(248, 238, 248);
}

  .back {
    position: fixed;
    top: 30px;
    right: 200px;
}

  .back a {
    padding: 10px 20px;
    color: white;
    border-radius: 4px;
    background-color: #FF4081;
    text-decoration: none;
}
</style>
