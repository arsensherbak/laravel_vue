<template>
    <div>
        <CreateComponent></CreateComponent>
        <IndexComponent></IndexComponent>
    </div>
</template>

<script>
import CommentComponent from "./CommentComponent";
import CreateComponent from "./CreateComponent";
import IndexComponent from "./IndexComponent";

export default {
    name: "PostComponent",
    components: {
        CommentComponent,
        CreateComponent,
        IndexComponent
    },
    data() {
        return {}
    },

    computed: {},

}
</script>

<style scoped>

</style>
