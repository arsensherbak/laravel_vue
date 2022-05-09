<template>
    <div>
        <div>
            <input type="text" v-model="name" placeholder="name" class="form-control">
        </div>
        <div>
            <input type="text" v-model="job" placeholder="job" class="form-control">
        </div>
        <div>
            <input type="text" v-model="age" placeholder="age" class="form-control">
        </div>
        <div>
            <input :disabled="!isDisable"  type="submit" value="Add" class="btn btn-primary" @click.prevent="storePerson">
        </div>
    </div>
</template>

<script>
import router from "../../router";

export default {
    name: "Create",
    data() {
        return {
            name: null,
            age: null,
            job: null,
        }
    },
    methods: {
        storePerson() {
            axios.post('/api/people', {name: this.name, age: this.age, job: this.job})
                .then(res => {
                    router.push({name: 'person.index'})
                })
        }
    },
    computed: {
        isDisable(){
            return this.name && this.age && this.job
        }
    }
}
</script>

<style scoped>

</style>
