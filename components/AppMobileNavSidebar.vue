<template>
    <div>
        <div class='mobile-header'>
            <div class='mobile-header__left'>
                <button @click.prevent = "active = !active" v-bind:class='{active:active}' class='mobile-header__nav-menu transform-button'>  
                </button>
            </div>
            <div class='mobile-header__logo'>
                <nuxt-link to="/">
                     <img class="global-header__logo " src="/png/logo.png" alt="">
                </nuxt-link>
            </div>
            <div class='mobile-header__right'>
                  <button class='button-nav' @click.prevent = "opened = !opened" id="openedCaretMobile">
                      <img class="global-header__exit" src="/png/home.png" alt="">
                  </button>  
            </div>
        </div>

        <div v-if='active' class='active-nab-bar'>
                <ul class="mobile-header__ul">
                    <li v-for='item in navMenu' class="mobile-header__li">
                        <span>{{item}}</span>
                    </li> 
                </ul>
        </div>
        <!-- <aside > -->
                 <authContainer v-if="opened"></authContainer>
        <!-- </aside> -->


        
    </div>
</template>
<script>
    export default {
        data() {
            return {
                active: false,
                opened: false
            }
        },
        watch: {
            active: function() {
                document.getElementsByClassName('global-header')[0].style.height = 'auto'
                document.getElementsByClassName('container')[0].style.overflow = 'hidden'
            }
        },
        computed: {
            navMenu () {
                return this.$i18n.messages.[this.$i18n.locale].navMenu
            }
        },
        mounted() {
         const onClickOutside = e => {
            this.opened = document.getElementById('openedCaretMobile').contains(e.target) && this.opened;
         } 
         document.addEventListener('click', onClickOutside);
         this.$on('hook:beforeDestroy', () => document.removeEventListener('click', onClickOutside));
        },
        components: {
            authContainer: () => import('./auth/authContainer') 
        }
    }
</script>