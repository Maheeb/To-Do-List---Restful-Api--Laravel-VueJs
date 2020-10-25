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
            <task-component v-for="task in tasks" :key="task.id" :task="task"></task-component>
            <tr>
                <td><input type="text" id="task" class="form-control"></td>
                <td>
                    <select name="" id="select" class="form-control">
                        <option value="">Low</option>
                        <option value="">Medium</option>
                        <option value="">High</option>
                    </select>
                </td>
                <td>
                    <button class="btn btn-primary">Add</button>
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

                message: "Hello from Maheeb..."
            }
        },
        created(){
            this.getTasks();
        },
        methods: {
            // getTasks() {
            //     window.axios.get('/api/tasks').then(({data})=>{
            //         data.forEach(task=>{
            //             this.tasks.push(task);
            //         });
            //
            //         }
            //     )
            // },

            getTasks(){
                window.axios.get('/api/tasks').then(({data})=>{

                    data.forEach(task=>{

                        this.tasks.push(task);
                    })


                })

            }


        },


        components: {TaskComponent}
    }
</script>

<style scoped>

</style>
