<template>
    <v-sheet class="mx-auto ma-10 text-center" height="auto" max-width="700">

        <h1 class="text-capitalize font-weight-black">
            {{ currentPost.title }}
        </h1>

        <h5 class="ma-7">
            Post Number {{ currentPost.id }}
        </h5>

        <v-img height="400px" src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg" cover></v-img>

        <p v-if="edit === true" class="ma-8">
            {{ currentPost.body }}
        </p>
    
        <v-textarea v-if="edit === false" class="ma-8"  maxlength="auto" :value="currentPost.body" >
        </v-textarea>

        <div class="d-flex flex-end">
            <v-btn class="mr-2" variant="tonal" @click="(edit = false)">
            Edit
        </v-btn>
        <v-btn variant="tonal" @click="store.commit('setCurrentPost', '')">
            Delete
        </v-btn>
        </div>


    </v-sheet>
</template>

<script setup>
import { computed } from "vue";
import { useStore } from "vuex";
import { ref } from 'vue'
import { onMounted } from "vue";

const store = useStore();
const currentPost = computed(() => store.getters.currentPost)
let edit = ref(true) 
</script>