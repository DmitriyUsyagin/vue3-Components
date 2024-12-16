<template>
    <div>
        <ul class="list">
            <li class="list-item">
                <div>
                    <p>
                        <strong> {{ comment.name }}</strong>
                    </p>
                    <small> e-mail: {{ comment.email }}</small>
                    <p>{{ comment.body }}</p>
                    <hr />
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: ["comment"],
    data() {
        return {};
    },

    computed: {},

    methods: {},

    mounted() {},

    components: {},
};
</script>

<style scoped></style>
