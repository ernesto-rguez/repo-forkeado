<script setup>
import InputError from '@/Components/InputError.vue';
import InputLabel from '@/Components/InputLabel.vue';
import ButtonGeneric from '@/Components/ButtonGeneric.vue';
import TextInput from '@/Components/TextInput.vue';
import { useForm } from '@inertiajs/vue3';
import { ref } from 'vue';

const passwordInput = ref(null);
const currentPasswordInput = ref(null);

const form = useForm({
    email: '',
    current_password: '',
    password: '',
    password_confirmation: '',
});

const props = defineProps({
    showP: {
        type: Boolean,
        default: false,
    },
    titulo:{
        type: String,
    }
});
const updatePassword = () => {
    form.put(route('password.update'), {
        preserveScroll: true,
        onSuccess: () => form.reset(),
        onError: () => {
            if (form.errors.password) {
                form.reset('password', 'password_confirmation');
                passwordInput.value.focus();
            }
            if (form.errors.current_password) {
                form.reset('current_password');
                currentPasswordInput.value.focus();
            }
        },
    });
};
</script>

<template>
      <div>
            <div v-if="props.showP" class="modal fade show " style="display: block;"  data-bs-backdrop="static" aria-labelledby="exampleModalLabel">
        <div class="modal-dialog modal-dialog-centered">
            <div class="modal-content">
                <div class="container-btn-close">
                    <a  data-bs-dismiss="modal" aria-label="Close" class="cursor-pointer"><i class="fa-regular fa-xmark"></i></a>
                </div>
                <div class="modal-header w-100">
                    <p class="modal-title">
                        Cambiar Contraseña
                    </p>
                </div>
                <div class="modal-body w-100">
                    <form @submit.prevent="updatePassword" class="mt-3 space-y-3">
                        <div>
                <InputLabel for="email" value="Ingrese usuario o correo*" />

                <TextInput
                    id="email"
                    ref="emailInput"
                    v-model="form.email"
                    type="email"
                    class="mt-1 block w-full input"
                    autocomplete="current-password"
                    placeholder="Nombre de usuario o correo"
                />

            </div>
                        <div>
                <InputLabel for="current_password" value="Contraseña Actual" />

                <TextInput
                    id="current_password"
                    ref="currentPasswordInput"
                    v-model="form.current_password"
                    type="password"
                    class="mt-1 block w-full input"
                    autocomplete="current-password"
                />

                <InputError :message="form.errors.current_password" class="mt-2" />
            </div>

            <div class="">
                <InputLabel for="password" value="Nueva Contraseña" />

                <TextInput
                    id="password"
                    ref="passwordInput"
                    v-model="form.password"
                    type="password"
                    class="mt-1 block w-full input"
                    autocomplete="new-password"
                />

                <InputError :message="form.errors.password" class="mt-2" />
            </div>

            <div>
                <InputLabel for="password_confirmation" value="Confirmar Nueva Contraseña" />

                <TextInput
                    id="password_confirmation"
                    v-model="form.password_confirmation"
                    type="password"
                    class="mt-1 block w-full input"
                    autocomplete="new-password"
                />

                <InputError :message="form.errors.password_confirmation" class="mt-2" />
            </div>

            <div class="flex items-center gap-4 pt-5">
                <ButtonGeneric :disabled="form.processing">Guardar</ButtonGeneric>

                <Transition
                    enter-active-class="transition ease-in-out"
                    enter-from-class="opacity-0"
                    leave-active-class="transition ease-in-out"
                    leave-to-class="opacity-0"
                >
                    <p v-if="form.recentlySuccessful" class="text-sm text-gray-600 dark:text-gray-400">Saved.</p>
                </Transition>
            </div>
        </form>
                </div>
            </div>
        </div>
    </div>
        </div>
    <section>
        <header>
            <h2 class="text-lg font-medium text-gray-900 dark:text-gray-100">Update Password</h2>

            <p class="mt-1 text-sm text-gray-600 dark:text-gray-400">
                Ensure your account is using a long, random password to stay secure.
            </p>
        </header>

       
    </section>
</template>
