<template>
<EnterData @addLink="addLink"/>
<h1>Your Links</h1>
<orderBy @sendData="sendData" @sendChecked="sendChecked"/>
<Content :vids="vids" @deleteRow="deleteRow"/>
</template>

<script>
import EnterData from '@/components/EnterData.vue'
import orderBy from "@/components/orderBy.vue"
import Content from '@/components/Content.vue'
export default {
  name: 'App',
  data(){
    return {
      id: 1,
      name: '',
      url: '',
      vids: [
        // {
        //   id: 1,
        //   name: 'n1',
        //   url: 'u1'
        // },
        // {
        //   id: 2,
        //   name: 'n2',
        //   url: 'u2'
        // },
        // {
        //   id: 3,
        //   name: 'n3',
        //   url: 'u3'
        // },
        // {
        //   id: 4,
        //   name: 'n4',
        //   url: 'u4'
        // },
        // {
        //   id: 5,
        //   name: 'n5',
        //   url: 'u5'
        // },
        // {
        //   id: 6,
        //   name: 'a',
        //   url: 'aa'
        // },
      ],
      originalVids: []
    }
  },
  emits: ['addLink','deleteRow'],
  components: {
    EnterData,
    orderBy,
    Content,
  },
  methods: {
    addLink(v){
      v.id = this.id,
      this.name = v.name,
      this.url = v.url,
      this.vids.push({id: this.id,name: this.name, url: this.url})
      this.id++
    },
    deleteRow(vid){
      this.vids = this.vids.filter((v) => v.name !== vid.name && v.url !== vid.url)
    },
    sendData(){
      let copy = [...this.vids]; // Create a copy of the array to sort
      copy.sort((a, b) => a.name.localeCompare(b.name)); // Sort by name
      this.vids = [...copy]
    },
    sendChecked(v){
      if (v.checked === true) {
      // If checked, reverse the array and update vids
      this.originalVids = [...this.vids];
      this.vids = [...this.vids].reverse();
    } else {
      // If unchecked, restore the original vids state
      this.vids = [...this.originalVids];
    }
    }
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
