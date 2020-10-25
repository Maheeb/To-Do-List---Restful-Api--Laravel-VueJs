<template>
    <div class="app-component">

        <table class="table">
            <thead>
            <tr>
                <th>Id</th>
                <th>Task Title</th>
                <th>Priority</th>
                <th>Action</th>
            </tr>
            </thead>
            <tbody>
            <task-component v-for="task in tasks" :key="task.id" :task="task" @delete="remove"></task-component>
            <tr>
                <td><input type="text" v-model="task.title" id="task" class="form-control"></td>
                <td>
                    <select v-model='task.priority' name="" id="select" class="form-control">
                        <option>Low</option>
                        <option>Medium</option>
                        <option>High</option>
                    </select>
                </td>
                <td>
                    <button @click="store" class="btn btn-primary">Add</button>
                </td>
            </tr>
            </tbody>
        </table>

    </div>

</template>

<script>
    import TaskComponent from './Task.vue'

    export default {

        data() {
            return {

                tasks: [],
                task: {title: '', priority: ''},

                message: "Hello from Maheeb..."
            }
        },
        created() {
            this.getTasks();
            // this.store();
        },
        methods: {

            getTasks() {
                window.axios.get('/api/tasks').then(({data}) => {

                    data.forEach(task => {

                        this.tasks.push(task);
                    })


                })

            },
            store() {
                if(this.checkInputs()) {
                    window.axios.post('/api/tasks', this.task).then(savedData => {

                        this.tasks.push(savedData.data);
                        this.task.title = '';
                    })
                }

            },
            checkInputs(){

                if(this.task.title && this.task.priority)
                    return true;


            },



            remove(id) {
                // console.log('The id is: '+ id);

                window.axios.delete(`/api/tasks/${id}`).then(() => {

                    let index = this.tasks.findIndex(task => task.id === id);

                    this.tasks.splice(index, 1);

                });


            }


        },


        components: {TaskComponent}
    }
</script>

<style scoped>

</style>
