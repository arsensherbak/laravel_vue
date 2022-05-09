<template>
    <div >
        <div >
            <router-link :to="{ name: 'person.index'}">Person</router-link>
            <router-link :to="{ name: 'person.create'}">Create</router-link>

            <router-view></router-view>
        </div>

    </div>
</template>

<script>
export default {
    name: "Index"
}
</script>

<style scoped>

</style>
