<template>
    <Head title="Login Page" />
    
    <main class="grid place-items-center min-h-screen" >
        <section class="bg-white p-8 rounded-xl max-w-md mx-auto border">
            <h1 class="text-3xl mb-6">Login</h1>
            <form @submit.prevent="submit" method="POST" action="/" class="">
                
                <div class="mb-6">
                    <label class="block mb-2 uppercase font-bold text-xs text-gray-700"
                            for="email"
                    >
                        E-mail
                    </label>
                    <input v-model="form.email" class="border p-2 w-full rounded"
                            type="email"
                            name="email"
                            id="email"
                            required
                    >
                    <div v-if="form.errors.email" v-text="form.errors.email" class="text-red-500 text-xs mt-1">
                    </div>
                </div>
                <!--PASSWORD-->
                <div class="mb-6">
                    <label class="block mb-2 uppercase font-bold text-xs text-gray-700"
                            for="password"
                    >
                        password
                    </label>
                    <input v-model="form.password" class="border p-2 w-full rounded"
                            type="password"
                            name="password"
                            id="password"
                            
                    >
                    <div v-if="form.errors.password" v-text="form.errors.password" class="text-red-500 text-xs mt-1">
                    </div>
                </div>
                <!--END OF PASSWORD-->

                <!--SUBMIT BUTTON-->
                <div class="mb-6">
                    <button type="submit" 
                            class="bg-blue-400 text-white rounded py-2 px-4 hover:bg-blue-500"
                            :disabled="form.processing"
                    >
                        Log In
                    </button>
                </div>
                <!--END OF SUBMIT BUTTON-->
            </form>
        </section>
    </main>
</template>

<script>
    export default {
        layout: null
    };
</script>

<script setup>
    import { useForm } from "@inertiajs/inertia-vue3";

    let form = useForm({
        email: '',
        password: ''
    })
    let submit = () =>{
        form.post('/login')
    }
</script>