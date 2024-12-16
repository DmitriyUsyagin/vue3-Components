<template>
    <div class="card card-w70">
        <div
            v-for="(content, index) in contents"
            :key="index"
        >
            <h1 v-if="content.type === 'title'">{{ content.value }}</h1>
            <h2 v-if="content.type === 'subtitle'">{{ content.value }}</h2>
            <img
                class="avatar"
                v-if="content.type === 'avatar'"
                :src="content.value"
                alt="Avatar"
            />
            <p v-if="content.type === 'text'">{{ content.value }}</p>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        contents: {
            type: Array,
            required: true,
        },
    },
    data() {
        return {
            active: this.contents.value,
        };
    },
};
</script>
<style scoped>
.preview {
    border: 1px solid #ccc;
    padding: 10px;
    width: 300px;
}
.preview h1 {
    margin: 0;
}
.preview img {
    max-width: 100%;
}
.avatar {
    width: 150px;
    height: 150px;
    border: 1px solid white;
    border-radius: 50%;
    object-fit: cover;
    object-position: center;
}
</style>
