<template>
    <div class="container column">
        <FormComponent @add-content="handleAddContent" />
        <app-content-def v-if="active"></app-content-def>
        <PreviewComponent
            v-else
            :contents="contents"
        />
    </div>
    <div class="container">
        <p>
            <button
                class="btn primary"
                @click="loadComments"
                v-if="!blockComments"
            >
                Загрузить комментарии
            </button>
        </p>
        <div
            class="card"
            v-if="blockComments"
        >
            <h2>Комментарии</h2>
            <appComments
                v-for="comment in comments"
                :key="comment.id"
                :comment="comment"
            ></appComments>
        </div>
        <app-loader v-if="loading"></app-loader>
    </div>
</template>

<script>
import appContentDef from "./components/appContentDef.vue";
import FormComponent from "./components/FormComponent.vue";
import PreviewComponent from "./components/PreviewComponent.vue";
import appLoader from "./components/appLoader.vue";
import axios from "axios";
import appComments from "./components/appComments.vue";

export default {
    data() {
        return {
            contents: [],
            active: true,
            comments: [],
            loading: false,
            blockComments: false,
        };
    },

    computed: {},

    methods: {
        handleAddContent(content) {
            this.contents.push(content);
            this.active = false;
        },
        async loadComments() {
            try {
                this.loading = true;
                const response = await axios.get(
                    "https://jsonplaceholder.typicode.com/comments?_limit=42",
                );
                this.comments = response.data;
                this.loading = false;
            } catch (error) {
                this.loading = false;

                console.error("ОШИБКА ПРИ ПОЛУЧЕНИИ КОММЕНТАРИЕВ", error);
            }
            this.blockComments = true;
        },
    },

    mounted() {},

    components: {
        FormComponent,
        PreviewComponent,
        appContentDef,
        appLoader,
        appComments,
    },
};
</script>

<style></style>
