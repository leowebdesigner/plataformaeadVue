<template>
    <li>
        <span :class="['card',bgName]">
            <span class="icon">
                <img :src="[course.image !='' ? course.image : require('@/assets/images/icons/default.png')]" :alt="title">
            </span>
            <span class="title">{{ course.name }}</span>
            <span class="action">
                <!-- <a href="trainings.html" :class="['btn', 'laravel']">Acessar</a> -->
                <!-- <router-link :to="{name: 'campus.modulos'}" :class="['btn', 'laravel']">
                Acessar
                </router-link> -->
                <a href="#" @click.prevent ="setCourse" :class="['btn', 'laravel']">Acessar</a>
            </span>
        </span>
        <span class="dots">
            <span></span>
            <span></span>
            <span></span>
        </span>
    </li>
</template>

<script>
import router from '@/router';

import { useStore } from 'vuex';

export default {
    name: "CardCourse",
    props: ['course','bgName'],
    setup(props){
        const store = useStore()

        const setCourse = () => {
           store.commit('SET_COURSE_SELECTED', props.course)

           router.push({name:'campus.modulos'})
        }
        return {
            setCourse
            }
    }
};

</script>