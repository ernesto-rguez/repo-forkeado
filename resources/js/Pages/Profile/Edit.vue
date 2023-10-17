<script setup>
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
import ModalPassWord from "./Partials/ModalPassWord.vue";
import ModalUser from "@/Pages/Profile/Partials/ModalProfile.vue";
import { Head } from "@inertiajs/vue3";
import { ref } from "vue";
import Show from "../Department/Show.vue";

const customroute = "profile.edit";
const showM = ref(false);
const showP = ref(false);
const titlesModal = ref("");

defineProps({
    mustVerifyEmail: {
        type: Boolean,
    },
    status: {
        type: String,
    },
    user: {
        type: Array,
        default: () => [],
    },
    guardian: {
        type: Array,
        default: () => [],
    },
    titles: {
        type: String,
    },
});


</script>

<template>
    <Head title="Profile" />

    <AuthenticatedLayout :croute="customroute">
        <div class="mx-auto">
            <h5 class="title text-dark text-bold fw-10">
                <span><i class="fas fa-chevron-left"></i></span> Mi Perfil
            </h5>
            <p class="" style="color: #757575">
                <span><i class="far fa-calendar"></i></span> Fecha de alta:
                <span>15/07/23 13:30h</span>
            </p>

            <div id="personal-data" class="col-11 mx-auto pt-5">
                <h5 class="text-dark mb-3">Datos personales</h5>
                <div class="card col-12 br-15 mx-auto">
                    <div
                        class="position-relative top-0 start-0 translate-middle mx-auto"
                    >
                        <img
                            :src="user.photo_url"
                            class="rounded-full w-20 object-cover"
                        />
                    </div>
                    <div class="row col-12">
                        <div class="col-lg-6">
                            <div class="p-2 col-11 mx-auto">
                                <div>
                                    <h5 class="text-dark fw-10 mb-0">
                                        Datos del responsable legal:<span
                                            ><button
                                                type="button"
                                                class="btn btn-transparent text-dark"
                                                @click="
                                                    (titlesModal =
                                                        'Datos Responsable Legal'),
                                                        (showM = true)
                                                "
                                            >
                                                <i
                                                    class="far fa-pencil"
                                                ></i></button
                                        ></span>
                                    </h5>
                                </div>
                                <div class="row ml-0">
                                    <div class="col-lg-6">
                                        <p class="mb-0 fw-10">
                                            Nombre y Apellido:
                                        </p>
                                        <p>Antony García Rodríguez</p>
                                    </div>
                                    <div class="col-lg-6">
                                        <p class="mb-0 fw-10">DNI:</p>
                                        <p>00-000-000</p>
                                    </div>
                                </div>
                                <div class="row ml-0">
                                    <div class="col-lg-6">
                                        <p class="mb-0 fw-10">
                                            Fecha de nacimiento:
                                        </p>
                                        <p>00/00/0000</p>
                                    </div>
                                    <div class="col-lg-6">
                                        <p class="mb-0 fw-10">Teléfono:</p>
                                        <p>00000000000</p>
                                    </div>
                                </div>
                                <div></div>
                            </div>
                        </div>
                        <div class="col-lg-6">
                            <div class="p-2 col-11 mx-auto">
                                <div>
                                    <h5 class="text-dark fw-10 mb-0">
                                        Datos del alumno:<span
                                            ><button
                                                type="button"
                                                class="btn btn-transparent text-dark"
                                                @click="
                                                    (titlesModal =
                                                        'Datos del Alumno'),
                                                        (showM = true)
                                                "
                                            >
                                                <i
                                                    class="far fa-pencil"
                                                ></i></button
                                        ></span>
                                    </h5>
                                </div>
                                <div class="row d-flex ml-0">
                                    <div class="col-lg-6">
                                        <p class="mb-0 fw-10">
                                            Nombre y Apellido:
                                        </p>
                                        <p>Aitana lopez García</p>
                                    </div>
                                    <div class="col-lg-6">
                                        <p class="mb-0 fw-10">DNI:</p>
                                        <p>00-000-000</p>
                                    </div>
                                </div>
                                <div class="row d-flex ml-0">
                                    <div class="col-lg-6">
                                        <p class="mb-0 fw-10">
                                            Fecha de nacimiento:
                                        </p>
                                        <p>00/00/0000</p>
                                    </div>
                                    <div class="col-lg-6">
                                        <p class="mb-0 fw-10">Teléfono:</p>
                                        <p>00000000000</p>
                                    </div>
                                </div>
                                <div></div>
                            </div>
                        </div>
                    </div>
                    <div class="row col-12">
                        <div class="p-2 col-11 mx-auto">
                            <div>
                                <h5 class="text-dark fw-10 mb-0">
                                    Usuario y Contraseña:<span
                                        ><button
                                            type="button"
                                            class="btn btn-transparent text-dark"
                                            @click="
                                                (showP = true),
                                                    (titlesModal =
                                                        'Cambiar Contraseña')
                                            "
                                        >
                                            <i
                                                class="far fa-pencil"
                                            ></i></button
                                    ></span>
                                </h5>
                            </div>
                            <div class="flex-row ml-0">
                                <div class="col-lg-4">
                                    <p class="mb-0">
                                        <span class="fw-10">Correo: </span>
                                        example@mail.com
                                    </p>
                                </div>
                                <div class="col-lg-4">
                                    <p>
                                        <span class="fw-10">Contraseña</span>
                                        **********
                                        <i class="fal fa-eye-slash"></i>
                                    </p>
                                </div>
                            </div>
                        </div>
                    </div>
                    <!-- <div>
                        <div class="p-5">
                            {{ guardian.name }} {{ guardian.surname }}
                            {{ guardian.email }}
                        </div>
                        <div class="p-5">
                            {{ user.name }} {{ user.surname }} {{ user.email }}
                        </div>
                    </div> -->
                </div>
            </div>
        </div>
        <div class="mx-auto">
            <div id="personal-data" class="col-11 mx-auto pt-3">
                <h5 class="text-dark mb-3">Datos acádemicos</h5>
                <div class="card col-12 br-15">
                    <div class="col-12 ml-0 mr-0">
                        <div>
                            <h5 class="text-dark fw-10 mb-0 py-3 text-center">
                                Asignaturas/ Plan de estudios:
                            </h5>
                        </div>
                        <div class="row col-12 mx-auto ml-0">
                            <table class="table table-borderless">
                                <thead>
                                    <tr>
                                        <th class="text-center">Asignaturas</th>
                                        <th>Profesor/a:</th>
                                        <th class="text-center">
                                            Calificación:
                                        </th>
                                        <th class="text-center">Nª de Aula</th>
                                        <th class="text-center">Asistencia</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr>
                                        <th class="text-center">
                                            Matemáticas Discretas
                                        </th>
                                        <td>Luis Pérez</td>
                                        <td class="text-center">8</td>
                                        <td class="text-center">2-A</td>
                                        <td class="text-center">10</td>
                                    </tr>
                                </tbody>
                            </table>
                            <nav aria-label="Page navigation example">
                                <ul class="pagination justify-content-center">
                                    <li class="page-item disabled">
                                        <a
                                            class="page-link"
                                            href="#"
                                            tabindex="1"
                                            aria-disabled="true"
                                            ><i class="fal fa-angle-left"></i
                                        ></a>
                                    </li>
                                    <li class="page-item">
                                        <a class="page-link" href="#">1</a>
                                    </li>
                                    <li class="page-item">
                                        <a class="page-link" href="#">2</a>
                                    </li>
                                    <li class="page-item">
                                        <a class="page-link" href="#">3</a>
                                    </li>
                                    <li class="page-item">
                                        <a class="page-link" href="#"
                                            ><i class="fal fa-angle-right"></i
                                        ></a>
                                    </li>
                                </ul>
                            </nav>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <ModalUser :show="showM" :title="titlesModal" :closeModalUser="closeModalUsers"> </ModalUser>
        <ModalPassWord :showP="showP"></ModalPassWord>
    </AuthenticatedLayout>
</template>
<style>
.text-dark {
    color: #2b5db6 !important;
}
.br-15 {
    border-radius: 20px;
    border: 0px !important;
    box-shadow: 1px 1px 10px rgb(228, 222, 222);
}
.fw-10 {
    font-weight: 600;
}
.w-20 {
    width: 8rem !important;
}
</style>
