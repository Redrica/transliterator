<template>
    <div class="hello">
        <h1>{{ msg }}</h1>
        <p class="text">
            Простой как валенок транслитератор
        </p>
        <p class="text text--small">(без специфических правил и вот этого всего)</p>
        <div class="section">
            <p class="section__text">Введите текст:</p>
            <textarea class="section__field"
                      v-model="originData"
            ></textarea>
            <t-button class="section__button"
                btn-text="Получите результат:"
                @button-click="convertText"
            ></t-button>
            <textarea class="section__field"
                v-model="translatedData"
            ></textarea>
        </div>
    </div>
</template>

<script>
    import TButton from "@/components/TButton";
    import { dictionary } from "@/scripts/constants";

    export default {
        name: "HelloWorld",

        components: {
            TButton,
        },

        props: {
            msg: String
        },

        data() {
            return {
                originData: '',
                translatedData: '',
            }
        },

        methods: {
            convertText() {
                let characters = this.originData.split('');
                this.translatedData = characters.map((i) => {
                    let isUp = i === i.toUpperCase();
                    let char = dictionary.get(i.toLowerCase()) || i;
                    if (isUp) {
                        char = char.replace(char[0], char[0].toUpperCase());
                    }
                    return i = char;
                }).join('');
            }
        }
    };
</script>

<style lang="scss">
    h3 {
        margin: 40px 0 0;
    }

    .text {
        max-width: 600px;
        margin: 20px auto;

        &--small {
            margin-top: -10px;
            font-size: 12px;
        }
    }

    .section {
        display: flex;
        flex-direction: column;
        width: fit-content;
        margin: 0 auto;

        @media (max-width: 600px) {
            width: auto;
        }
    }

    .section__text {
        margin: 15px 0;
        text-align: left;
        font-weight: 700;
    }

    .section__field {
        width: 600px;
        height: 150px;
        margin-bottom: 25px;
        resize: vertical;

        @media (max-width: 600px) {
            width: 100%;
        }

        &:hover,
        &:focus {
            border: 2px solid #41b883;
            outline: none;
        }
    }

    .section__button {
        margin: 0 auto 15px 0;
    }


</style>
