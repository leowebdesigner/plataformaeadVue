<template>

    <section id="loginPage" :style="{ backgroundImage: 'url(' + require('@/assets/images/bgLogin.jpg') + ')' }">
        <div class="loginContent">
            <div class="loginCard">
                <div class="decor" style="background-image: url('./assets/images/building.jpg');">
                    <div class="content">
                        <span class="logo">
                            <img :src="require('@/assets/images/imagelogin.png')" alt="Léo web designer">
                        </span>
                        <span class="dots">
                            <span></span>
                            <span></span>
                            <span></span>
                        </span>
                        <span class="description">
                            <p>
                                Os melhores e mais completos cursos de Laravel do Brasil, cursos com projetos reais. Do
                                zero ao profissional.
                            </p>
                        </span>
                        <span class="copyright fontSmall">
                            Todos os Direitos reservados - <b>Léo Web Designer</b>
                        </span>
                    </div>
                </div>
                <div class="login">
                    <div class="content">
                        <span class="logo">
                            <img :src="require('@/assets/images/logo.png')" alt="Léo Web Designer">
                        </span>
                        <span>
                            <p>Seja muito bem vindo(a)!</p>
                        </span>
                        <span class="dots">
                            <span></span>
                            <span></span>
                            <span></span>
                        </span>
                        <span class="description">
                            Acesse nossa plataforma e desfrute de cursos completos para sua especialização.
                        </span>
                        <form action="/dist/index.html" method="">
                            <div class="groupForm">
                                <i class="far fa-envelope"></i>
                                <input type="email" name="email" placeholder="Email" v-model="email" required>
                            </div>
                            <div class="groupForm">
                                <i class="far fa-key"></i>
                                <input type="password" name="password" placeholder="Senha" v-model="password" required>
                                <i class="far fa-eye buttom"></i>
                            </div>
                            <button :class="[
                                'btn',
                                'primary',
                                loading ? 'loading' : ''
                            ]" 
                            type="submit" @click.prevent="auth">
                                <span v-if="loading">alterando...</span>
                                <span v-else>Atualizar Senha</span>
                            </button>
                        </form>
                    </div>
                    <span class="copyright fontSmall">
                        Todos os Direitos reservados - <b>Léo WebDesigner</b>
                    </span>
                </div>
            </div>
        </div>
    </section>

</template>

<script>

import { ref } from 'vue'

import router from '@/router'
import ResetPasswordService from '@/services/password.reset'

export default {

    name: 'ResetPassword',
    props:{
        token:{
            require: true,

        }
    },
    setup(props) {

        const email = ref("")
        const password = ref("")
        const loading = ref(false)

        const auth = () => {
            loading.value = true

            ResetPasswordService.reset ({
                email: email.value,
                password: password.value,
                token: props.token
            })
            .then(() => router.push({name: 'auth'}))
            .catch(() => alert('error'))
            .finally(() => loading.value = false)
        }
        return {
            auth,
            email,
            password,
            loading,
        }
    }
}
</script>