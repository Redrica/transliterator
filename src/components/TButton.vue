<template>
    <button
        class="t-button"
        :class="classes"
        @click="onButtonClick"
    >{{ btnText }}</button>
</template>

<script>
    export default {
        name: "Tbutton",

        props: {
            classes: {
                type: String,
                default: '',
            },
            btnText: {
                type: String,
                default: 'Кнопка',
            }
        },

        methods: {
            onButtonClick() {
                this.$emit('button-click', true);
            },
        }
    }
</script>

<style lang="scss">
    .t-button {
        padding: 10px 15px;
        border: none;
        border-radius: 0;
        background-color: #41b883;
        color: white;
        font: inherit;

        &:hover,
        &:focus {
            background-color: saturate(#41b883, 20);
            outline: none;
        }
    }
</style>