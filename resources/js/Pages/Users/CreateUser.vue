<script setup lang="ts">
import { useForm, Link } from '@inertiajs/vue3'
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue'
import InputError from '@/Components/Forms/InputError.vue'
import InputText from '../../Components/Forms/InputText.vue'

const form = useForm({
    name: '',
    document: '',
    password: '',
})

function submit() {
    form.post(route('users.store'))
}
</script>

<template>
    <AuthenticatedLayout title="Criar Usuário">
        <template #actions>
            <Link class="btn btn-primary" :href="route('users.index')">
                Voltar
            </Link>
        </template>
        <form @submit.prevent="submit">
            <div class="card card-default">
                <div class="card-body">
                    <div class="mb-3">
                        <InputText
                            id="name"
                            v-model="form.name"
                            type="text"
                            label="Nome *"
                            required
                            autofocus
                            autocomplete="name" />

                        <InputError class="mt-2" :message="form.errors.name" />
                    </div>

                    <div class="mb-3">
                        <InputText
                            id="document"
                            v-model="form.document"
                            type="text"
                            label="CPF *"
                            required
                            autocomplete="document" />

                        <InputError class="mt-2" :message="form.errors.document" />
                    </div>

                    <div class="mb-3">
                        <InputText
                            id="password"
                            v-model="form.password"
                            type="password"
                            label="Senha"
                            autocomplete="new-password" />

                        <InputError class="mt-2" :message="form.errors.password" />
                    </div>
                </div>
                <div class="card-footer">
                    <button type="submit" class="btn btn-primary" :disabled="form.processing">
                        Criar Usuário
                    </button>
                </div>
            </div>
        </form>
    </AuthenticatedLayout>
</template>
