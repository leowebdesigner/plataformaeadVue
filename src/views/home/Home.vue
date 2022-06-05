<template>
  <div>
    <div class="pageTitle">
      <span class="title">Meus Cursos</span>
      <span class="dots">
        <span></span>
        <span></span>
        <span></span>
      </span>
    </div>

    <div class="content">
      <ul class="listCourses">
        <card-course 
        v-for = "courses in myCourses"
        :key = "courses.id"
        :bgName="'bg-laravel'"
        :course ="courses">
        </card-course>
      </ul>
    </div>
  </div>
</template>

<script>
import { onMounted, computed } from 'vue'; 
import { useStore } from 'vuex';

import CardCourse from './components/CardCourse.vue'

export default {

  name: "Home",
  setup (){
    const store = useStore()
    
    const myCourses = computed(()=> store.state.courses.myCourses )
    
    onMounted(() => store.dispatch('getCourses'))
      
    return{
      myCourses
    } 
  },

  components: {
    CardCourse
              }
};

</script>
