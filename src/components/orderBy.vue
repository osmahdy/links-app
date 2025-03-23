<template>
    <div>
        <label>Order By:</label>
    <select  v-model="type" @change="sendData">
        <option disabled value="">Type</option>
            <option value="name">Name</option>
            <option value="id">Id</option>
    </select>
    <section>
        <input type="checkbox" v-model="checked" id="rev" :checked="checked" @change="sendChecked">
        <label for="rev">Reverse</label>
    </section>
</div>
    
</template>

<script>
export default {
    name: 'orderBy',
    data(){
        return {
            type: "id",
            checked: false,
        }
    },
    methods: {
        sendData(){
            this.$emit('sendData',{
                type: this.type,
            })
        },
        sendChecked(){
            this.$emit('sendChecked',{
                checked: this.checked,
            })
        }
    }
}
</script>

<style scoped>
div {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 500px;
    margin: auto;
}
label {
    font-size: 20px;
    font-weight: bold;

}
select {
    width: 150px;
    font-size: 18px;
    background-color: #9370db;
    color: white;
    border: 0;
    outline: none;
    padding: 10px;
    margin: 10px 0;
    border-radius: 5px;
    cursor: pointer;
    transition: .3s;
}
select option:first-child {
    font-weight: bold;
}
select option {
    padding: 10px;
}
select option:disabled {
    color: white;
    font-weight: bold;
}
</style>