<template>
    <div id='photo-baner'>
        <div class="photo-baner__title">
            <h1>{{$t('title')}}</h1> 
            <h3>{{$t('subTitle')}}</h3>
        </div>
         <div class="photo-baner__buttons">
             <button class="photo-baner__button button-nav">{{$t('button.weddingPhotographers')}}</button>
             <button class="photo-baner__button button-nav">{{$t('button.familyPhotographers')}}</button>
         </div>       
         <!-- 
             h сімейні історії 
             p риба текст бла бла бла 
              дві кнопки сімейний фотограф весільний фотограф 
             background фото з былим фоном  \

             фото аватар пятикутник 
             під ним 5 фотографій
             
          -->
    </div>
</template>

<script>
export default {
    data() {
        return {

        }
    },
    mounted() {
        // this.changeBaner()
         
    },
    methods: {
        changeBaner() {
            const baner = document.getElementById('photo-baner')
            let counter = 1
            setInterval(() => {
                counter++
                if (counter === 11) counter = 1
                baner.style.backgroundImage = `url('/baner/baner${counter}.jpg')`
            }, 50000);
        }
    },
}
</script>