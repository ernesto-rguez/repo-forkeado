<script setup>
import TextInput from '@/Components/TextInput.vue'
import ButtonGeneric from '../../../Components/ButtonGeneric.vue';
import { useForm } from '@inertiajs/vue3';
import { onMounted } from 'vue';

const form = useForm({
    fullName: 'Ulises Cabrales',
    dni:'00-000-000',
    birthDay: '12/12/2012',
    phone: ''


})
const props = defineProps({
    show: {
        type: Boolean,
        default: false,
    },
    title:{
        type: String,
    }
});

onMounted(()=>{
    document.addEventListener('keyup',(event) =>{
        console.log('close event');
        if(event.key == 'Escape'){
            closeModal()
        }
    })
})
const emits = defineEmits(['update:show']);

const closeModal = () => {
    emits('update:show', false)
    console.log(props.show)
}



</script>
<template>
    <div class="row">
        
        
        <div>
            <div v-if="props.show" class="modal fade show " style="display: block;"  data-bs-backdrop="static" aria-labelledby="exampleModalLabel">
        <div class="modal-dialog modal-dialog-centered">
            <div class="modal-content">
                <div class="container-btn-close">
                    <button  @click="closeModal()" aria-label="Close" class="cursor-pointer"><i class="fa-regular fa-xmark"></i></button>
                </div>
                <div class="modal-header w-100">
                    <p class="modal-title">
                        <slot name="modal-header"></slot>
                    </p>
                </div>
                <div class="modal-body w-100">
                    <form action="">
                         <slot name="modal-body">
                       <h3 class="text-dark text-center" >Editar Perfil</h3>
                       <h5 class="text-center" v-text="titulo"></h5>
                       <div class="pt-3">
                        <label for="" class="mb-1 w-200">Nombre y Apellido</label>
                        <TextInput class="input" type="text" v-model="form.fullName" id="input-fullName"></TextInput>
                       </div>
                       <div class="d-flex pt-3">
                        <div class="pr-1">
                        <label for="" class="mb-1">DNI</label>
                        <TextInput class="input" v-model="form.dni" id="input-dnm"></TextInput>
                       </div>
                       <div class="pl-1">
                        <label for="" class="mb-1">Fecha de Nacimiento</label>
                        <TextInput class="input" type="date" v-model="form.birthDay" id="input-birthday"></TextInput>
                       </div>
                       </div>
                       <div class="pt-3">
                        <label for="" class="mb-1">Teléfono</label>
                        <TextInput class="input" type="tel" v-model="form.phone" id="input-phone"></TextInput>
                       </div>
                       <div class="pt-8 text-center">
                        <ButtonGeneric class="full-width col-12" @click="closeModal">Guardar</ButtonGeneric>
                    </div>
                    </slot>
                   
                    </form>
                   
                </div>
            </div>
        </div>
    </div>
        </div>
    </div>
</template> 
<style>
.input {
    display:flex ;
    width: 100% ;
    height: 3.2rem ;
    border-radius: 3rem;
    border: 1px solid #2b5db6 ;
    background-color: #fff  ;
    font-size: 1.3rem   ;
    text-align: center ;
}
.container-btn-close{
    width: 100%;
    display: flex;
    flex-direction: row-reverse;
}
.fa-xmark{
    color: #3C7FF8;
    font-size: 1.5rem;
}

.modal {
    background: rgba(0, 0, 0, 0.45);
    z-index: 1200;
}

.modal-content {
    display: flex;
    border-radius: 3.125rem;
    border: 3px solid #3C7FF8;
    background: #FFF;
    height: 45rem;
    padding: 3.5rem 5.5rem;
    flex-direction: column;
    align-items: flex-start;
}

div.modal-dialog.modal-dialog-centered {
    max-width: 35rem;
}

.modal-header {
    display: flex;
    justify-content: center;
    align-items: center;
    border: 0;
}

.modal-title {
    color: #3c7ff8;
    font-size: 2rem;
    font-weight: 600;
}
.modal-body{
    padding: 0;
}



</style>
