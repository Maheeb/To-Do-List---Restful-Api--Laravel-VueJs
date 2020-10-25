<template>
    <div class="app-component">

        <table class="table">
            <thead>
            <tr>
                <th>Task Title</th>
                <th>Priority</th>
                <th>Action</th>
            </tr>
            </thead>
            <tbody>
            <task-component></task-component>
            <tr>
                <td><input type="text" id="task" class="form-control"></td>
                <td>
                    <select name="" id="select" class="form-control">
                        <option value="">Low</option>
                        <option value="">Medium</option>
                        <option value="">High</option>
                    </select>
                </td>
                <td><button class="btn btn-primary">Add</button></td>
            </tr>
            </tbody>
        </table>

    </div>

</template>

<script>
    import TaskComponent from  './Task.vue'
    export default {

        data() {
            return {
                message: "Hello from Maheeb..."
            }
        },
        components: {TaskComponent}
    }
</script>

<style scoped>

</style>
