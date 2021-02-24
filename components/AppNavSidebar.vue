<template>
<div class='nav-menu'>
    <ul class='nav-menu__ul'>
         <li class="nav-menu__logo">
             <nuxt-link to="/">
                 <img class="global-header__logo" src="/png/logo.png" alt="">
              </nuxt-link>
         </li>
         <li v-for= 'item in navMenu' class="nav-menu__item">
             <span>{{item}}</span>
         </li> 
         <li class="nav-menu__item">
             <button @click.prevent = "opened = !opened" class="button-nav" id="openedCaret">
                 <img class="global-header__exit" src="/png/home.png" alt="">
             </button>
             <aside v-if="opened">
                 <span class="nav-menu__caret">test</span>
                 <authContainer></authContainer>
             </aside>
         </li> 
    </ul>

</div>
    
</template>
<script>
export default {
    data() {
        return {
            opened: false
        }
    },
    mounted() {
         const onClickOutside = e => {
            this.opened = document.getElementById('openedCaret').contains(e.target) && this.opened;
         } 
         document.addEventListener('click', onClickOutside);
         this.$on('hook:beforeDestroy', () => document.removeEventListener('click', onClickOutside));
    },
    computed: {
        navMenu () {
         return this.$i18n.messages.[this.$i18n.locale].navMenu
        }
    },
    components: {
        authContainer: () => import('./auth/authContainer') 
    }
}
</script>