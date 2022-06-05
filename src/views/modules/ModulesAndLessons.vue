<template>

    <div class="pageTitle">
        <span class="title">{{course.name}}</span>
        <span class="dots">
            <span></span>
            <span></span>
            <span></span>
        </span>
    </div>

    <div class="content">
        <div class="container">

            <modules />

            <div class="right">
                <div class="content">

                  <player/>
                  <supports-lesson/>

                </div>
            </div>
        </div>
    </div>

</template>

<script>
import { useStore } from 'vuex'
import { computed } from 'vue'

import Modules from './components/Modules.vue'
import Player from './components/Player.vue'
import SupportsLesson from './components/SupportsLesson.vue'

export default {
    name: 'ModulesAndLesson',
    setup(){
      const store = useStore()

      const course = computed(() => store.state.courses.courseSelected)

      return{ 
          course
      }
    },
    components: {
        Modules,
        Player,
        SupportsLesson
                }
}
</script>