<template>
    <ul class='nav-menu__container'>
         <li v-for = '(li, index) in auth' class="nav-menu__li">   
             <button class="nav-menu__button" @click.prevent = 'goToAuth(index)'> 
                 <span>{{li}}</span>
             </button>
         </li>
    </ul>
</template>

<script>
export default {

    data() {
        return {
        }
    },
    computed: {
        auth () {
             return this.$i18n.messages.[this.$i18n.locale].auth
        }
    },
    methods: {
        goToAuth(index) {
            this.$root.$emit('auth', index)
            // this.$router.push(`/${index}`)
        }
    },
}
</script>