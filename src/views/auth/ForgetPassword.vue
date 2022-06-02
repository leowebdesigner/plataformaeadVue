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
                                <input type="email" name="email" placeholder="Email" required>
                            </div>

                            <button class="btn primary" type="submit">Recuperar Senha</button>
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
export default {
    name: 'ForgetPassword',


}
</script>