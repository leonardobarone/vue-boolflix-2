<template>
    <header class="container-fluid">
        <div class="row align-items-center">
            <h1 class="col-2">
                L
                <hide-at breakpoint="small">EOFLIX</hide-at>
            </h1>
            <form class="col-10 text-align-right search">
                <input v-model="searchText" type="text" placeholder="Cerca film o serie tv">
                <button type="submit" @click.prevent="$emit('searching', searchText)">Cerca</button>
            </form>
        </div>
    </header>
</template>

<script>
import { hideAt } from 'vue-breakpoints';

export default {
    name: 'Header',
    components: { 
        hideAt, 
    },
    data() {
        return { 
            searchText: ""
        }
    }
}
</script>

<style lang="scss" scoped>
header {
    padding: 10px;
    position: fixed;
    top: 0px;
    z-index: 1;
    background-color: var(--nero);
    
    h1 {
        color: var(--rosso);
    }
    
    .search {

        input, button {
            padding: 5px;
            margin-left: 5px;
        }

        button {
            color: white;
            border: 1px solid white;
            background-color: var(--nero);
            cursor: pointer;
        }
    
    }
}
</style>