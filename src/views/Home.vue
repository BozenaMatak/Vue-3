<template>
  <div class="row">
    <div class="col-8">

      <InstagramCard :key="card.id" v-for="card in filteredCards" :info="card"/>

    </div>
    <div class="col-4">
      Mi smo sidebar
    </div>
  </div>
</template>

<script>
import InstagramCard from '@/components/InstagramCard.vue'
import store from '@/store.js'

export default {
  name: 'home',
   data() {   
      return {     
         cards: [       
           { title: 'jedan', time: 'an hour ago',  ime: 'Lucija',  url: 'https://picsum.photos/id/1/400/400' }, 
            { title: 'dva', time: '2 days ago', ime: 'Ines', url: 'https://picsum.photos/id/2/400/400' }  
          ]  
       }
      },
     computed: {    
       filteredCards() {      
         return this.cards.filter((card) => {
          return card.title.match(store.searchTerm)|| card.time.match(store.searchTerm)|| card.ime.match(store.searchTerm)})
       }
      },
  components: {
    InstagramCard
  }
}
</script>

<style lang="scss">

.card-body {
  padding: 0px;
}

</style>