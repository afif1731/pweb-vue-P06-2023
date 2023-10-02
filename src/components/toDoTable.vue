<template>
    <body>
        <div class="createBtn">
            <button id="createButton" data-bs-toggle="modal"><p>Create</p></button>
        </div>
        <div class="todo">
        <table class="doTable">
            <thead>
                <tr>
                    <th>No</th>
                    <th>To-Do List</th>
                    <th>Category</th>
                    <th>Checklist</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody v-for="(task, index) in tdListAction.tdListRill">
                <tr v-if="task.sdh == 0">
                    <th>{{ index+1 }}</th>
                    <th>{{ task.tdo }}</th>
                    <th>{{ task.kategori }}</th>
                    <th class="checklist-box"><svg v-if="task.sdh == 0" @click="tdListAction.moveToDone(task.doNum)" xmlns="http://www.w3.org/2000/svg" width="32" height="32" fill="currentColor" class="bi bi-square" viewBox="0 0 16 16">
                                                <path d="M14 1a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1h12zM2 0a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2H2z"/>
                                                </svg></th>
                    <th>
                        <div class="actionBtn">
                            <router-link :to="{name: 'edit', params: {doNum : task.doNum}}">
                                <svg xmlns="http://www.w3.org/2000/svg" height="1.2em" viewBox="0 0 512 512"
                                    class="cursor-pointer">
                                    <path
                                        d="M471.6 21.7c-21.9-21.9-57.3-21.9-79.2 0L362.3 51.7l97.9 97.9 30.1-30.1c21.9-21.9 21.9-57.3 0-79.2L471.6 21.7zm-299.2 220c-6.1 6.1-10.8 13.6-13.5 21.9l-29.6 88.8c-2.9 8.6-.6 18.1 5.8 24.6s15.9 8.7 24.6 5.8l88.8-29.6c8.2-2.7 15.7-7.4 21.9-13.5L437.7 172.3 339.7 74.3 172.4 241.7zM96 64C43 64 0 107 0 160V416c0 53 43 96 96 96H352c53 0 96-43 96-96V320c0-17.7-14.3-32-32-32s-32 14.3-32 32v96c0 17.7-14.3 32-32 32H96c-17.7 0-32-14.3-32-32V160c0-17.7 14.3-32 32-32h96c17.7 0 32-14.3 32-32s-14.3-32-32-32H96z" />
                                </svg>
                            </router-link>
                            <svg 
                                @click="tdListAction.deleteTd(task.doNum)"
                                xmlns="http://www.w3.org/2000/svg" height="1.2em" viewBox="0 0 448 512"
                                class="cursor-pointer">
                                <path
                                    d="M135.2 17.7L128 32H32C14.3 32 0 46.3 0 64S14.3 96 32 96H416c17.7 0 32-14.3 32-32s-14.3-32-32-32H320l-7.2-14.3C307.4 6.8 296.3 0 284.2 0H163.8c-12.1 0-23.2 6.8-28.6 17.7zM416 128H32L53.2 467c1.6 25.3 22.6 45 47.9 45H346.9c25.3 0 46.3-19.7 47.9-45L416 128z" />
                            </svg>
                        </div>
                    </th>
                </tr>
            </tbody>
        </table>
        </div>
        <div>

        </div>
        <div class="todone">
        <table class="doneTable">
            <thead>
                <tr>
                    <th>No</th>
                    <th>Done List</th>
                    <th>Category</th>
                    <th>Checklist</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody v-for="(task, index) in tdListAction.tdListDoneRill">
                <tr v-if="task.sdh == 1">
                    <th>{{ index+1 }}</th>
                    <th>{{ task.tdo }}</th>
                    <th>{{ task.kategori }}</th>
                    <th class="checklist-box"><svg v-if="task.sdh==1" @click="tdListAction.moveToDo(task.doNum)" xmlns="http://www.w3.org/2000/svg" width="32" height="32" fill="currentColor" class="bi bi-check-square" viewBox="0 0 16 16">
                                                <path d="M14 1a1 1 0 0 1 1 1v12a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1h12zM2 0a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V2a2 2 0 0 0-2-2H2z"/>
                                                <path d="M10.97 4.97a.75.75 0 0 1 1.071 1.05l-3.992 4.99a.75.75 0 0 1-1.08.02L4.324 8.384a.75.75 0 1 1 1.06-1.06l2.094 2.093 3.473-4.425a.235.235 0 0 1 .02-.022z"/>
                                                </svg></th>
                    <th>
                        <div class="actionBtn">
                            <svg 
                                @click="tdListAction.deleteTdDone(task.doNum)"
                                xmlns="http://www.w3.org/2000/svg" height="1.2em" viewBox="0 0 448 512"
                                class="cursor-pointer">
                                <path
                                    d="M135.2 17.7L128 32H32C14.3 32 0 46.3 0 64S14.3 96 32 96H416c17.7 0 32-14.3 32-32s-14.3-32-32-32H320l-7.2-14.3C307.4 6.8 296.3 0 284.2 0H163.8c-12.1 0-23.2 6.8-28.6 17.7zM416 128H32L53.2 467c1.6 25.3 22.6 45 47.9 45H346.9c25.3 0 46.3-19.7 47.9-45L416 128z" />
                            </svg>
                        </div>
                    </th>
                </tr>
            </tbody>
        </table>
        </div>
    </body>
</template>

<style scoped>
/* Reset default margin and padding for the entire page */
*{
    margin: 0;
    padding: 0;
    background-color: white;
    font-family: 'Righteous', cursive;
}

h1, h2, h3, p, ul, li {
    margin: 0;
    padding: 0;
}

body {
    margin: 0 5%;
    padding: 0;
}


/* Style for Create button */
.createBtn {
    display: block;
}

#createButton {
    float: right;
    border: none;
    margin: 20px 0;
}

#createButton p {
    color: #fff;
    background-color: #485664;
    border: none;
    border-radius: 5px;
    padding: 3px 10px;
    font-weight: bold;
    font-size: 35px;
}

.todo {
    min-height: 500px;
}
.todone {
    margin: 3em 0 5em;
}

table {
    width: 100%;
    margin: 20px auto 0;
    border: 1px solid black;
    border-collapse: collapse;
}

thead {
    border: 1px solid black;
    align-items: center;
}

thead th {
    position: static;
    background-color: #dbdbdb;
    font-size: 20px;
    font-weight: 600;
}

th {
    color: rgb(20, 19, 19);
    text-align: center;
    padding: 10px;  
}

tbody th {
    background-color: whitesmoke;
    font-size: 18px;
    font-weight: lighter;
}

.doneTable tbody th{
    color: rgba(0, 0, 0, 30%);
    text-decoration: line-through;
    text-decoration-thickness: 2px;
}

.checklist-box{
    text-align: center;
}
.checklist-box input{
    width: 25px;
    height: 25px;
}
.actionBtn {
    background-color: rgba(0, 0, 0, 0);
}
.actionBtn a{
    background-color: rgba(0, 0, 0, 0);
}
.actionBtn svg {
    background-color: rgba(0, 0, 0, 0);
    padding: 0 10%;
}

</style>

<script>
import { tdListAction } from '../assets/doTable';

export default {
    data() {
        return {
            tdListAction,
        }
    },
    mounted() {
        if(localStorage.length == 0) {
            tdListAction.setLclStrg();
        } else {
            for(let task in localStorage) {
                let doList = localStorage.getItem(task);
                if (doList !== null) {
                    doList=JSON.parse(doList)
                    if (doList.sdh == 0) tdListAction.addTd(doList)
                    else if (doList.sdh == 1) tdListAction.addTdDone(doList)
                }
            }
        }
    }
}
</script>