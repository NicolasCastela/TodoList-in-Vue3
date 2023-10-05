<template>
    <div class="bodyhome">
        <div class="containerpai">
            <h1>TODOLIST</h1>
            <form @submit.prevent="adicionarTarefa">
                <input v-model="tarefa" placeholder="Digite aqui sua Tarefa" type="text">
                <button type="submit">Enviar</button>
            </form>
        </div>
        <div class="containerlista">
            <ul>
                <li class="cadatarefa" v-for="(tarefa, id ) in tarefas" :key="id">{{ tarefa }} ID: {{ id +1 }} <button @click="excluirtarefa(id)">Delete</button> </li>
            </ul>
        </div>
    </div>
</template>
<!--  -->
<script>
export default {
    name: 'Lista',
    data() {
        return {
            tarefa: "",
            tarefas: []
        }
    },
    methods: {
        adicionarTarefa() {
            if (this.tarefa.trim() !== "") {
                this.tarefas.push(this.tarefa);
                this.tarefa = ""; 
            }
        },

        excluirtarefa(index) {
        this.tarefas.splice(index, 1);
    }
}


} /*Final export */

</script>

<style scoped>
.containerlista {
    height:200px;
    width: 400px;
    background-color: gainsboro;
}

.bodyhome {
    background-color: #296b1c;
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    height: 100vh;
}

.containerpai {
    height: 250px;
    width: 400px;
    background-color: gainsboro;
    display: flex;
    justify-content: center;
    flex-direction: column;
}

.containerpai button {
    width: 200px;
    background-color: #77c867;
    color: white;
    font-weight: 700;
    font-size: 14px;
    transition: 0.5s;
    padding: 6px;
    border: none;
    box-shadow: 1px 1px 4px rgb(108, 106, 106);
}

.containerpai button:hover {
    background-color: #296b1c;
    transition: 0.5s;
}

.containerpai input {
    width: 300px;
    height: 30px;
    border: 1px solid rgb(105, 97, 97);
    border-radius: 5px;
    margin-bottom: 15px;
    box-shadow: 0 0 0 0;
    border: 0 none;
    outline: 0;
    text-align: center;

    margin-top: 20px;

}
.cadatarefa{
    list-style: none;
    text-align: start;
    background-color: white;
    width: 80%;
    display: flex;
    justify-content: space-between;
    height: 50px;
    border-radius: 5px;
    border: none;
    align-items: center;
    margin-bottom: 4px;
}
</style>