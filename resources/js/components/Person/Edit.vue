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
            <input :disabled="!isDisable"  type="submit" @click.prevent="updatePerson" value="Edit" class="btn btn-primary">
        </div>
    </div>
</template>

<script>
import router from "../../router";
export default {
    name: "Edit",
    data() {
        return {
            name: null,
            age: null,
            job: null,
        }
    },
    mounted() {
        this.getPerson()

    },
    methods: {
        getPerson() {
            axios.get(`/api/people/${this.$route.params.id}`)
                .then(res => {
                    console.log(res);
                    this.name = res.data.data.name
                    this.age = res.data.data.age
                    this.job = res.data.data.job
                })
        },
        updatePerson(){
            axios.patch(`/api/people/${this.$route.params.id}`, {name: this.name, age: this.age, job: this.job})
            .then(res=> {
                router.push({name: 'person.show', params:{ id: this.$route.params.id} })
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
