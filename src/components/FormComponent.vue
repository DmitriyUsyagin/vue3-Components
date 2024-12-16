<template>
    <div class="card card-w30">
        <div class="form-control">
            <label for="type">Тип блока</label>
            <select
                v-model="selectedType"
                id="type"
            >
                <option value="title">Заголовок</option>
                <option value="subtitle">Подзаголовок</option>
                <option value="avatar">Аватар</option>
                <option value="text">Текст</option>
            </select>
        </div>

        <div class="form-control">
            <label for="value">Значение</label>
            <textarea
                id="value"
                rows="3"
                v-model.trim="inputText"
            ></textarea>
        </div>

        <button
            class="btn primary"
            @click="addContent"
            :disabled="this.inputText.length < 3"
        >
            Добавить
        </button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            selectedType: "title",
            inputText: "",
        };
    },

    computed: {},

    methods: {
        addContent() {
            const content = {
                type: this.selectedType,
                value: this.inputText,
            };

            this.$emit("add-content", content);

            this.inputText = "";
        },
    },

    mounted() {},

    components: {},
};
</script>

<style scoped></style>
