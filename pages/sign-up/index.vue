<template>
    <div class="auth">
        <div class="auth__form">
            <ul>
                <li v-for='(item, index) in typeAuth'>
                    <nuxt-link :to="'/sign-up/' + index">
                        {{item}}
                    </nuxt-link>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    
    computed: {
        typeAuth () {
             return this.$i18n.messages.[this.$i18n.locale].typeAuth
        }
    },
}
</script>