<template>

    <div class="w-full pt-10 px-4 sm:px-6 md:px-8 lg:pl-72">
        <div v-if="loading" class="flex justify-center items-center h-screen">
            <div role="status">
                <!-- SVG spinner -->
                <svg aria-hidden="true" class="w-8 h-8 mr-2 text-gray-200 animate-spin dark:text-gray-600 fill-blue-600" viewBox="0 0 100 101" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M100 50.5908C100 78.2051 77.6142 100.591 50 100.591C22.3858 100.591 0 78.2051 0 50.5908C0 22.9766 22.3858 0.59082 50 0.59082C77.6142 0.59082 100 22.9766 100 50.5908ZM9.08144 50.5908C9.08144 73.1895 27.4013 91.5094 50 91.5094C72.5987 91.5094 90.9186 73.1895 90.9186 50.5908C90.9186 27.9921 72.5987 9.67226 50 9.67226C27.4013 9.67226 9.08144 27.9921 9.08144 50.5908Z" fill="currentColor"/>
                    <path d="M93.9676 39.0409C96.393 38.4038 97.8624 35.9116 97.0079 33.5539C95.2932 28.8227 92.871 24.3692 89.8167 20.348C85.8452 15.1192 80.8826 10.7238 75.2124 7.41289C69.5422 4.10194 63.2754 1.94025 56.7698 1.05124C51.7666 0.367541 46.6976 0.446843 41.7345 1.27873C39.2613 1.69328 37.813 4.19778 38.4501 6.62326C39.0873 9.04874 41.5694 10.4717 44.0505 10.1071C47.8511 9.54855 51.7191 9.52689 55.5402 10.0491C60.8642 10.7766 65.9928 12.5457 70.6331 15.2552C75.2735 17.9648 79.3347 21.5619 82.5849 25.841C84.9175 28.9121 86.7997 32.2913 88.1811 35.8758C89.083 38.2158 91.5421 39.6781 93.9676 39.0409Z" fill="currentFill"/>
                </svg>
                <span class="sr-only">Loading...</span>
            </div>

            <!-- You can use a spinner or any other loading animation here -->
        </div>

        <div v-else class="flex flex-col pt-10">
            <h2 class="text-4xl dark:text-white pb-10">
                Editar Familiar
            </h2>

            <EmployeeMenu />

            <div class="mt-3">
                <div id="bar-with-underline-1" role="tabpanel" aria-labelledby="bar-with-underline-item-1">
                    <div class="flex flex-col bg-white border shadow-sm rounded-xl dark:bg-gray-800 dark:border-gray-700 dark:shadow-slate-700/[.7]">
                        <form @submit.prevent="updateFamilyEmployee">
                            <div class="bg-gray-100 border-b rounded-t-xl py-3 px-4 md:py-4 md:px-5 dark:bg-gray-800 dark:border-gray-700">
                                <p class="mt-1 text-sm text-gray-500 dark:text-gray-500">
                                    Datos Personales
                                </p>
                            </div>
                            <div class="grid md:grid-cols-3 sm:grid-cols-12 gap-4 p-4 md:p-5">
                                <div>
                                    <label for="hs-validation-name-error" class="block text-sm font-medium mb-2 dark:text-white">RUT</label>
                                    <input
                                        type="text"
                                        id="rut_input"
                                        class="bg-white-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                        placeholder="RUT"
                                        v-model="rut_input"
                                        required
                                        @blur="onRutBlur"
                                        />
                                </div>
                                <div>
                                    <label for="hs-validation-name-error" class="block text-sm font-medium mb-2 dark:text-white">Nombres</label>
                                    <input
                                        type="text"
                                        id="names_input"
                                        class="bg-white-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                        placeholder="Nombres"
                                        v-model="names_input"
                                        required
                                        />
                                </div>
                                <div>
                                    <label for="hs-validation-name-error" class="block text-sm font-medium mb-2 dark:text-white">Apellido Paterno</label>
                                    <input
                                        type="text"
                                        id="father_lastname_input"
                                        class="bg-white-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                        placeholder="Apellido Paterno"
                                        v-model="father_lastname_input"
                                        required
                                        />
                                </div>
                            </div>
                            <div class="grid md:grid-cols-3 sm:grid-cols-12 gap-4 p-4 md:p-5">
                                <div>
                                    <label for="hs-validation-name-error" class="block text-sm font-medium mb-2 dark:text-white">Apellido Materno</label>
                                    <input
                                        type="text"
                                        id="mother_lastname_input"
                                        class="bg-white-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                        placeholder="Apellido Materno"
                                        v-model="mother_lastname_input"
                                        required
                                        />
                                </div>
                                <div>
                                    <label for="hs-validation-name-error" class="block text-sm font-medium mb-2 dark:text-white">Genero</label>
                                    <select v-model="gender_input" required class="bg-white-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                                        <option value="">- Genero -</option>
                                        <option value="1">Masculino</option>
                                        <option value="2">Femenino</option>
                                    </select>
                                </div>
                                <div>
                                    <label for="hs-validation-name-error" class="block text-sm font-medium mb-2 dark:text-white">Fecha de Nacimiento</label>
                                    <input
                                        type="date"
                                        id="born_date_input"
                                        class="bg-white-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                        placeholder="Fecha de Nacimiento"
                                        v-model="born_date_input"
                                        required
                                        />
                                </div>
                            </div>
                            <div class="grid md:grid-cols-3 sm:grid-cols-12 gap-4 p-4 md:p-5">
                                <div>
                                    <label for="hs-validation-name-error" class="block text-sm font-medium mb-2 dark:text-white">Parentesco</label>
                                    <select v-model="family_type_input" required class="bg-white-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
                                        <option value="">- Parentesco -</option>
                                        <option value="1">Conyugue</option>
                                        <option value="2">Hijo(a)</option>
                                        <option value="3">Padre</option>
                                        <option value="4">Madre</option>
                                    </select>
                                </div>
                                <div>
                                    <label for="hs-validation-name-error" class="block text-sm font-medium mb-2 dark:text-white">Certificado de Nacimiento</label>
                                    <input type="file" name="file-input-medium" id="file-input-medium" class="block w-full border border-gray-200 shadow-sm rounded-md text-sm focus:z-10 focus:border-blue-500 focus:ring-blue-500 dark:bg-slate-900 dark:border-gray-700 dark:text-gray-400
                                    file:bg-transparent file:border-0
                                    file:bg-gray-100 file:mr-4
                                    file:py-3 file:px-4
                                    dark:file:bg-gray-700 dark:file:text-gray-400"
                                    @change="handleFileChange"
                                    >
                                </div>
                                
                            </div>
                            <div class="grid md:grid-cols-8 sm:grid-cols-12 gap-4 p-4 md:p-5">
                                <div v-if="loading" class="flex items-center justify-center h-full">
                                    <div role="status">
                                        <!-- SVG spinner -->
                                        <svg aria-hidden="true" class="w-8 h-8 mr-2 text-gray-200 animate-spin dark:text-gray-600 fill-blue-600" viewBox="0 0 100 101" fill="none" xmlns="http://www.w3.org/2000/svg">
                                        <path d="M100 50.5908C100 78.2051 77.6142 100.591 50 100.591C22.3858 100.591 0 78.2051 0 50.5908C0 22.9766 22.3858 0.59082 50 0.59082C77.6142 0.59082 100 22.9766 100 50.5908ZM9.08144 50.5908C9.08144 73.1895 27.4013 91.5094 50 91.5094C72.5987 91.5094 90.9186 73.1895 90.9186 50.5908C90.9186 27.9921 72.5987 9.67226 50 9.67226C27.4013 9.67226 9.08144 27.9921 9.08144 50.5908Z" fill="currentColor"/>
                                        <path d="M93.9676 39.0409C96.393 38.4038 97.8624 35.9116 97.0079 33.5539C95.2932 28.8227 92.871 24.3692 89.8167 20.348C85.8452 15.1192 80.8826 10.7238 75.2124 7.41289C69.5422 4.10194 63.2754 1.94025 56.7698 1.05124C51.7666 0.367541 46.6976 0.446843 41.7345 1.27873C39.2613 1.69328 37.813 4.19778 38.4501 6.62326C39.0873 9.04874 41.5694 10.4717 44.0505 10.1071C47.8511 9.54855 51.7191 9.52689 55.5402 10.0491C60.8642 10.7766 65.9928 12.5457 70.6331 15.2552C75.2735 17.9648 79.3347 21.5619 82.5849 25.841C84.9175 28.9121 86.7997 32.2913 88.1811 35.8758C89.083 38.2158 91.5421 39.6781 93.9676 39.0409Z" fill="currentFill"/>
                                        </svg>
                                        <span class="sr-only">Loading...</span>
                                    </div>
                                </div>
                                <div v-else class="w-full">
                                    <button type="submit" class="py-3 px-4 inline-flex justify-center items-center gap-2 rounded-md border border-transparent font-semibold bg-green-500 text-white hover:bg-green-600 focus:outline-none focus:ring-2 focus:ring-green-500 focus:ring-offset-2 transition-all text-sm dark:focus:ring-offset-gray-800">
                                        Actualizar
                                        <i class="fa-solid fa-check"></i>
                                    </button>
                                </div>
                                
                                <router-link
                                    :to="`/uniform_data_employee/${$route.params.rut}`"
                                    class="py-3 px-4 py-3 px-4 inline-flex justify-center items-center gap-2 rounded-md border font-medium bg-white text-gray-700 shadow-sm align-middle hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-white focus:ring-blue-600 transition-all text-sm dark:bg-slate-900 dark:hover:bg-slate-800 dark:border-gray-700 dark:text-gray-400 dark:hover:text-white dark:focus:ring-offset-gray-800"
                                >
                                    Cancelar
                                    <i class="fa-solid fa-remove"></i>
                                </router-link>
                            </div>
                        </form>
                    </div>
                </div>
                    
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios';
import EmployeeMenu from '../components/EmployeeMenu.vue';


export default {
    components: {
        EmployeeMenu
    },
    data() {
        return {
            loading: false,
            rut_input: '',
            names_input: '',
            father_lastname_input: '',
            mother_lastname_input: '',
            gender_input: '',
            born_date_input: '',
            family_type_input: '',
            birth_certificate: null,
        };
    },
    async created() {
        this.getFamilyDataEmployee();
    },
    methods: {
        async getFamilyDataEmployee() {
            const accessToken = localStorage.getItem('accessToken');

            this.loading = true;

            try {
                const response = await axios.get('http://localhost:8000/family_core_data/edit/' + this.$route.params.rut + '/1', {
                    headers: {
                        Authorization: `Bearer ${accessToken}`
                    },
                });
                console.log(response.data.message);
                this.rut_input = response.data.message.rut;
                this.names_input = response.data.message.names;
                this.father_lastname_input = response.data.message.father_lastname;
                this.mother_lastname_input = response.data.message.mother_lastname;
                this.gender_input = response.data.message.gender_id;
                this.born_date_input = response.data.message.born_date;
                this.family_type_input = response.data.message.family_type_id;

                this.loading = false;
            } catch (error) {
                if (error.message == "Request failed with status code 401") {
                    localStorage.removeItem('accessToken');
                    window.location.reload();
                } else {
                    console.error('Error al obtener los datos del familiar:', error);
                }
            }
        },
        handleFileChange(event) {
            // Access the selected file from the event object
            const selectedFile = event.target.files[0];

            // Do something with the selected file, such as storing it in the component's data or uploading it to a server.
            // For example, you can assign it to the data property 'birth_certificate':
            this.birth_certificate = selectedFile;
        },
        updateFamilyEmployee() {
            this.loading = true;

            var employee_rut = this.$route.params.id;
            var employee_rut = employee_rut.split("-");
            var numeric_employee_rut = employee_rut[0];

            const formData = new FormData();
            formData.append('family_type_id', this.family_type_input);
            formData.append('employee_rut', numeric_employee_rut);
            formData.append('gender_id', this.gender_input);
            formData.append('rut', this.rut_input);
            formData.append('names', this.names_input);
            formData.append('father_lastname', this.father_lastname_input);
            formData.append('mother_lastname', this.mother_lastname_input);
            formData.append('born_date', this.born_date_input);

            if (this.birth_certificate != null) {
                formData.append('support', this.birth_certificate);
            }

            const accessToken = localStorage.getItem('accessToken');

            // Make the POST request using axios
            axios.patch('http://localhost:8000/family_core_data/update/'+ this.$route.params.id, formData, {
                headers: {
                    Authorization: `Bearer ${accessToken}`,
                    'Content-Type': 'multipart/form-data', // Add this line for file upload
                },
            }).then(response => {
                console.log(response);
                this.loading = false;

                localStorage.setItem('updated_family', 1);

                this.$router.push('/family_data_employee/' + this.$route.params.rut);
            }).catch(error => {
                console.error(error);
                this.loading = false;
            });
        },
    },
}
</script>
