<template>
    <table>
        <thead>
            <td>ID</td>
            <td>Name</td>
            <td>Url</td>
            <td>Delete</td>
        </thead>
        <tr v-for="(vid) in vids" :key="vid.id">
            <td>#{{ vid.id }}</td>
            <td>{{ vid.name }}</td>
            <td>{{ vid.url }}</td>
            <td @click="deleteRow(vid)">X</td>
        </tr>
    </table>
</template>

<script>
export default {
    name: 'ContentTable',
    emits: ['deleteRow'],
    props: {
       vids: {
        type: Array,
        required: true
       }
    },
    components: {
       
    },
    methods: {
        deleteRow(vid){
            this.$emit('deleteRow',{
                id: vid.id,
                name: vid.name,
                url: vid.url
            })
        }
    }
}
</script>


<style scoped>
table {
    margin: 20px auto;
}
thead td {
    background-color: #ddd;
    color: black;
    padding: 10px;
    min-width: 150px;
    font-size: 20px;
    font-weight: bold;
}
tr td {
    background-color: #eee;
    color: black;
    padding: 10px;
    font-size: 18px;
}
tr td:last-child {
    color: red;
    font-weight: bold;
    cursor: pointer;
    transition: .3s;
}
tr td:last-child:hover {
    opacity: .7;
}
</style>