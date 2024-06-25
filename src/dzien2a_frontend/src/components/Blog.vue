<template>
<div>
<button @click="pobierzWpisy">refresh</button>
siema blog!
{{ wpisy }}
</div>
</template>

<script>
import { dzien2a_backend } from 'declarations/dzien2a_backend/index';

export default {
    data(){
        return {
            wpisy: []
        }
    },
    methods: {
        async pobierzWpisy(){
            this.wpisy = await dzien2a_backend.odczytaj_wpisy();
        }
    },
}
</script>