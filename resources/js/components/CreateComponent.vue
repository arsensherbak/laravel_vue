<template>
    <div class="col-6">
        <div class="mb-3">
            <input type="text" class="form-control" v-model="name" id="name" placeholder="name">
        </div>
        <div class="mb-3">
            <input type="number" class="form-control" v-model="age" id="age" placeholder="name">
        </div>
        <div class="mb-3">
            <input type="text" class="form-control" v-model="job" id="job" placeholder="name">
        </div>
        <div class="mb-3">
            <input @click.prevent="addPerson" type="submit" class="btn btn-primary" value="Go">
        </div>
    </div>
</template>

<script>
export default {
    name: "CreateComponent",
    data() {
        return {
            name: null,
            age: null,
            job: null,
        }
    },
    methods: {
        addPerson() {
            axios.post('/api/people', {name: this.name, age: this.age, job: this.job})
                .then(res => {
                    this.name = null
                    this.age = null
                    this.job = null
                    console.log(res);
                })
        }
    }
}
</script>

<style scoped>

</style>
