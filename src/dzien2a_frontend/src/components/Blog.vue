<template>
        <button @click="pobierzWpisy">refresh</button>
        siema blog!
        {{ wpisy }}
        <input v-model="nowyBlog" type="text">
        <button @click="dodajWpisy">dodaj</button>
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

}
</script>