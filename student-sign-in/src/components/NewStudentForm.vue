<template>
    <div>
    <!--Template/HTML here-->

    <div class="card add-student m-2 p-2">
        <h4 class="card-title">Add new student</h4>

        <div class="form-group">
            <label for="name">Name</label>
            <!-- v-model newStudentName -->
            <input id="name" class="form-control" v-model.trim="newStudentName">
        </div>
        <div class="form-group">
            <label for="starID">Star ID</label>
            <!-- v-model newStarID -->
            <input id="starID" class="form-control" v-model.trim="newStarID">
        </div>
            <!-- v-on:click event handler -->
            <button class="btn btn-primary" v-on:click="addStudent">Add</button>
    </div>

    </div>
</template>

<script>
export default {
    name:'NewStudentForm' ,
    emits: ['student-added'], // Document events this component emits
    date() {
        return {
            newStudentName:'' ,
            newStarID:'' ,
            errors: []
        }
    },
    methods: {
        addStudent() {
            this.errors = []

            if (!this.newStudentName) {
                this.errors.push('Student name is required')
            }
                
            if (!this.newStarID) {
                this.errors.push('StarId is required')
            }

            if (this.errors.length == 0) {
                let student = { name: this.newStudentName, starID: this.newStarID, present: false }


                // Emit message to parent with new student 
                this.$emit('Student-added', student)

                this.newStudentName = ''
                this.newStarID = ''
            }
            
        }
    }
}
</script>

<style scoped>

</style>