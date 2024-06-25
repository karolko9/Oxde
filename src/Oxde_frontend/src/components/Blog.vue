<template>
    <div>
        <button @click="pobierzWpisy">refresh</button>
        siema blog!
        {{ wpisy }}
        <input v-model="nowyBlog" type="text">
        <button @click="dodajWpisy">dodaj</button>
    </div>
</template>

<script>
import { Oxde_backend } from 'declarations/Oxde_backend/index';

export default {
    data() {
        return {
            wpisy: [],
            nowyBlog: ""
        }
    },
    methods: {
        async dodajWpisy() {
            await Oxde_backend.dodaj_wpis(this.nowyBlog);
        },
        async pobierzWpisy() {
            this.wpisy = await Oxde_backend.odczytaj_wpisy();
        }
    },

}
</script>