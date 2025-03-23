<template>
    <div class="parent">
        <div class="son">
            <label for="name">Video Name:</label>
            <input v-model="name" ref="input1" type="text" id="name" placeholder="Enter the video name">
        </div>
        <div class="son">
            <label for="url">Video Url:</label>
            <input v-model="url" ref="input2" type="text" id="url" placeholder="Enter the video url">
        </div>
        <button @click="add">Save</button>
    </div>
</template>


<script>
export default {
    name: 'EnterData',
    data(){
        return {
            name: '',
            url: '',
            value: '',
        }
    },
    methods: {
        add (){
            this.$refs.input1.value = ""
            this.$refs.input2.value = ""
            this.$emit('addLink',{
                name: this.name,
                url: this.url
            })
        }
    }
}
</script>

<style scoped>
.parent {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    background-color: #9370db80;
    padding: 20px;
    /* background-color: #483d8b; */
}
.son {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 500px;
    margin: 10px 0;
}
label {
    font-weight: bold;
    font-size: 22px;
    color: black;
}
input {
    all: unset;
    width: 350px;
    height: 50px;
    background-color: white;
    border-radius: 15px;
    border-bottom: 4px solid black;
    font-size: 18px;
    color: black;
}
button {
    width: 150px;
    font-size: 18px;
    background-color: #9370db;
    color: white;
    border: 0;
    padding: 10px;
    border-radius: 15px;
    margin: 10px 0;
    cursor: pointer;
    transition: .3s;
}
button:hover {
    opacity: .8;
}
</style>