<template>
    <form class="form" @submit.prevent="submit">
        <h1>Добавить рецепт</h1>
        <div v-if="visible">
            <div class="input">
                <input type="text" placeholder="Название рецепта" v-model="form.title">
            </div>
            <div class="input">
                <input type="text" placeholder="Описание рецепта" v-model="form.description">
            </div>
        </div>

        <div class="buttons">
            <button class="btn" type="submit" :disabled="!isValid">Создать</button>
            <button class="btn secondary" type="button" @click="toggle">
                {{ visible ? 'Убрать' : 'Показать'}} форму
            </button>
        </div>
    </form>
</template>

<script>
    import { useToggle } from '@/hooks/toggle'
    import { useForm } from '@/hooks/form'

    export default {
        props: {
            onAdd: {
                type: Function,
                required: true
            }
        },
        setup(props) {
            return {
                ...useForm(props),
                ...useToggle()
            }
        }
    }
</script>

<style scoped>
    .form {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 1rem;
        border: 1px solid #eee;
        margin-bottom: 1rem;
    }

    .form h1 {
        margin: 0;
        margin-bottom: 1rem;
    }

    .input {
        margin-bottom: 1rem;
    }

    .input input {
        border: 1px solid #ccc;
        border-radius: 5px;
        padding: 5px 8px;
        width: 400px;
    }

    .buttons {
        width: 400px;
        display: flex;
        justify-content: space-around;
    }
</style>
