<template>
    <div>
        <table class="table col-6" >
            <thead>
            <tr>
                <th scope="col">Name</th>
                <th scope="col">Age</th>
                <th scope="col">Job</th>
                <th scope="col">Edit</th>
                <th scope="col">delete</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="person in people">
                <td>{{ person.name }}</td>
                <td>{{ person.age }}</td>
                <td>{{ person.job }}</td>
                <td>
                    <router-link :to="{name: 'person.edit', params:{ id: person.id }}">Edit</router-link>
                </td>
                <td><a href="#" class="btn btn-outline-danger" @click.prevent="deletePeople(person.id)">Delete</a></td>
            </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: "Index",
    data() {
        return {
            people: null
        }
    },
    mounted() {
        this.getPeople()
    },
    methods: {
        getPeople() {
            axios.get('/api/people')
                .then(res => {
                    this.people = res.data.data
                })
        },
        deletePeople(id){
            axios.delete(`/api/people/${id}`)
            .then(res=>{
                this.getPeople()
            })
        }
    },
}
</script>

<style scoped>

</style>
