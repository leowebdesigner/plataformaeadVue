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
                            <p>Perdeu sua senha? Recupere-a agora mesmo!</p>
                        </span>
                        <span class="dots">
                            <span></span>
                            <span></span>
                            <span></span>
                        </span>
                        <span class="description">
                            Preencha o e-mail do cadastro abaixo
                        </span>
                        <form action="/dist/index.html" method="">
                            <div class="groupForm">
                                <i class="far fa-envelope"></i>
                                <input type="email" name="email" placeholder="Email" v-model="email" required>
                            </div>

                             <button :class="[
                                'btn',
                                'primary',
                                loading ? 'loading' : ''
                            ]" 
                            type="submit" @click.prevent="forgetPassword">
                                <span v-if="loading">Enviando...</span>
                                <span v-else>Recuperar Senha</span>
                            </button>
                        </form>
                        <span>
                            <p class="fontSmall">Acessar sua conta?
                                <router-link :to="{ name: 'auth' }" class="link primary">Clique aqui</router-link>
                            </p>
                        </span>
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
import { notify } from '@kyvg/vue3-notification'
import { ref } from 'vue'
import { useStore } from 'vuex'

export default {
    name: 'ForgetPassword',
    setup(){
        const store = useStore()
        const email = ref("")
        const loading = ref(false)

        const forgetPassword = () => {
            loading.value = true
            store.dispatch('forgetPassword', {email: email.value})
            .then(() => notify({
            title: 'Confira seu e-mail',
            text: 'Enviamos um link com a redefinição para o e-mail cadastrado',
            type: "warn"
            }))
            .catch(() =>  notify({
            title: 'Falha ao autenticar',
            text: 'Falha ao recuperar o usuário',
            type: "warn"
            }))
            .finally(() => loading.value = false)

        }

        return {
            email,
            forgetPassword,
            loading
        }
    }


}
</script>