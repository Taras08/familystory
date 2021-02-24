<template>
    <div class='global-header global-container'>
        <div>
                
        </div>    
        <AppNavSidebar ></AppNavSidebar>
        <AppMobileNavSidebar></AppMobileNavSidebar>
        <div>
        </div>
         </div>
</template>
<script>

    export default {
    data() {
        return {
        }
    },
    
    computed: {
      availableLocales () {  
             return this.$i18n.locales.filter(i => i.code !== this.$i18n.locale)
        }
    },
    components: {
        AppNavSidebar: ()=> import('./AppNavSidebar'),
        AppMobileNavSidebar: ()=> import('./AppMobileNavSidebar')
    }
}
</script>