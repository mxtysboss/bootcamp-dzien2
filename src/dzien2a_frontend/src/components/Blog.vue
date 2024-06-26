<template>
<div>
<h3 class="text-blue-600">Wpisy na blogu</h3>
        <button @click="pobierzWpisy">refresh</button>
        <div v-for="wpis in wpisy">
        <p>{{ wpis }}</p>
        </div> 
        <input v-model="nowyBlog" type="text">
        <button @click="dodajWpisy">dodaj</button>
        </div>
</template>

<script>
import { dzien2a_backend } from 'declarations/dzien2a_backend/index';

export default {
    data() {
        return {
            wpisy: [],
            nowyBlog: ""
        }
    },
    methods: {
        async dodajWpisy() {
            await dzien2a_backend.dodaj_wpis(this.nowyBlog);
        },
        async pobierzWpisy() {
            this.wpisy = await dzien2a_backend.odczytaj_wpisy();
        }
    },
    async mounted(){
        this.pobierzWpisy()
    }

}
</script>