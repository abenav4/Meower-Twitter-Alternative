<template>
  <q-page class="relative">
    <q-scroll-area class="absolute full-width full-height">
      <div class ="q-px-md q-py-lg row items-end q-col-gutter-md">
        <div class="col">
        <q-input bottom-slots v-model="newMeowContent" placeholder="compose your meow here!" counter maxlength="280" autogrow class="newMeow">
            <template v-slot:before>
              <q-avatar size="xl">
                <img src="https://i.pinimg.com/564x/3d/5b/1b/3d5b1b274d570b6535b9ffbbe4824b33.jpg">
              </q-avatar>
            </template>
          </q-input>
        </div>
        <div class="col col-shrink">
              <q-btn @click="addNewMeow" :disable="!newMeowContent" class="q-mb-lg" unelevated rounded color="primary" label="meow" no-caps/>          
        </div>
        </div>
        <q-separator class="divider" color="pink-1" size="10px"/>

        <q-list separator>
          <transition-group
            appear
            enter-active-class="animated fadeIn"
            leave-active-class="animated fadeOut"   
            >  
        <q-item v-for="meow in meows" :key="meow.date" class="q-py-md">
          <q-item-section avatar>
              <q-avatar size="xl">
                <img src="https://i.pinimg.com/564x/3d/5b/1b/3d5b1b274d570b6535b9ffbbe4824b33.jpg">
              </q-avatar>
          </q-item-section>

          <q-item-section>
            <q-item-label class="text-subtitle1"><strong>hasanabi apologist</strong>
            </q-item-label>
            <span class="text-grey-7"> @meowth</span>
            <q-item-label class="meow-content">
            {{meow.content}}
            </q-item-label>

            <div class="row meow-icons justify-between q-mt-sm">
              <q-btn flat round color="primary" size="sm" icon="far fa-comment" />
              <q-btn flat round color="primary" size="sm" icon="fas fa-retweet" />
              <q-btn flat round color="primary" size="sm" icon="far fa-heart" />
              <q-btn @click="deleteMeow(meow)" flat round color="primary" size="sm" icon="fas fa-trash" />
            </div>
          </q-item-section>
          <q-item-section side top>
            {{ meow.date }}
          </q-item-section>
        </q-item>
        </transition-group> 
      </q-list>
    </q-scroll-area>
    </q-page>
    
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'PageHome',
  data() {
    return {
      newMeowContent: '',
      meows: [
        {
          content: 'good meowning everynyan !!',
          date: 1659788143079
        },
        {
          content: 'remember to stay pawsitive owo',
          date: 1659788367652
        },
      ]
    }
  },
  methods: {
    addNewMeow() {
      let newMeow = {
        content: this.newMeowContent,
        date: Date.now()
      }
      this.meows.unshift(newMeow)
      this.newMeowContent=""
    }, 
    deleteMeow(meow) {
      let deleteDate = meow.date
      let index = this.meows.findIndex(meow => meow.date=deleteDate)
      this.meows.splice(index, 1)
    }
  }
})
</script>

<style lang="sass">
.newMeow
  textarea
    font-size: 19px
    line-height: 1.4
.divider
  border-top: 1px solid
  border-bottom: 1px solid
  border-color: $grey-4
.meow-content
  white-space: pre-line
.meow-icons
  margin-left:-5px
</style>

