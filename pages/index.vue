<template>
  <section class='home-page'>
    <AppPhotoBaner></AppPhotoBaner>
    <AppPhotographer></AppPhotographer> 
    <div class='test'>
      <a
                v-for="locale in $i18n.locales"
                :href="switchLocalePath(locale.code)"
                :key="locale.code">
                 {{ locale.code }}
            </a>
    </div>
    
  </section>
</template>

<script>

export default {

components: {
  AppPhotoBaner: () => import('../components/home/AppPhotoBaner'),
  AppPhotographer: () => import('../components/home/AppPhotographer')   
}
}
</script>

<style>
.test {
  height:600px;
  border: 2px solid #35495e;
  background-color: aquamarine;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
