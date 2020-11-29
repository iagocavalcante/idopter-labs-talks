---
marp: true
theme: gaia
_class: lead
paginate: true
color: #3eaf7c
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.jpg')
---

![bg left:40% 80%](https://pbs.twimg.com/media/EiNmaOCXsAI2sp-.png)

# **Vue 3 - Já vue ?**

Vue 3.0 - One Piece

[Vue3 site](https://v3.vuejs.org/guide/introduction.html)

---

# BrainStorm

- Inspirado fortemente pelos hooks do React
![bg right:50% 100%](https://dental-college.s3.amazonaws.com/presentations/vue-brainstorming.png)

---

# Principais mudanças

* Reescrito com typescript: decisão tomada para melhor escalar e ter um core manutenível
* Nova engine de renderização usando um novo algoritmo para o shadow DOM
* Novo compilador pro template. Ex.: [Template Explorer](https://vue-next-template-explorer.netlify.app/#%7B%22src%22%3A%22%3Cdiv%3E%5Cn%20%20%3Ch1%3EHello%20World!%3C%2Fh1%3E%5Cn%20%20%3Cp%3ETeste%3C%2Fp%3E%5Cn%3C%2Fdiv%3E%5Cn%22%2C%22options%22%3A%7B%22mode%22%3A%22module%22%2C%22prefixIdentifiers%22%3Afalse%2C%22optimizeImports%22%3Afalse%2C%22hoistStatic%22%3Afalse%2C%22cacheHandlers%22%3Afalse%2C%22scopeId%22%3Anull%2C%22inline%22%3Afalse%2C%22ssrCssVars%22%3A%22%7B%20color%20%7D%22%2C%22bindingMetadata%22%3A%7B%22TestComponent%22%3A%22setup-const%22%2C%22setupRef%22%3A%22setup-ref%22%2C%22setupConst%22%3A%22setup-const%22%2C%22setupLet%22%3A%22setup-let%22%2C%22setupMaybeRef%22%3A%22setup-maybe-ref%22%2C%22setupProp%22%3A%22props%22%2C%22vMySetupDir%22%3A%22setup-const%22%7D%7D%7D)
* API's expostas *


---

# Principais mudanças - Fragments

```HTML
<!-- Antes -->
<template>
  <div>
    <p>Esse são dois</p>
    <p>elementos roots</p>
  </div>
</template>
```

```HTML
<!-- Depois -->
<template>
  <p>Esse são dois</p>
  <p>elementos roots</p>
</template>
```

---

# Principais mudanças - Teleport

```HTML
<!-- Componente Navbar -->
<template>
  <header>
    <div id="portal-magico" />
  </header>
</template>

<!-- Outro componente -->
<template>
  <page>
    <Teleport to="portal-magico">
      <button class="portal-item">Notificação</button>
    </Teleport>
  </page>
</template>
```

---

# Principais mudanças - Suspense

```HTML
<template>
  <Suspense>
    <template #default>
      <data-table />
    </template>
    <template #fallback>
      <loading-gears />
    </template>
  </Suspense>
</template>
```

---

# Principais mudanças - Remoção da Global Vue
Antes:
```Js
import Vue from 'vue';
import Vuex from 'vuex';
import App from './App.vue';

Vue.use(Vuex);
const store = new Vuex.store({});
 new Vue({
  store,
  render: (h) => h(App),
}).$mount('#app');
```

---

# Principais mudanças - Remoção da Global Vue
Depois:

```Js
import { createApp } from 'vue';
import { createStore } from 'vuex';
import App from './App.vue';
 const store = createStore({});
 createApp(App)
  .use(store)
  .mount('#app');

```

---

- Forma de criar componente com Vue 2 
```JS
<template>
  <p @click="increaseCounter">{{ count }}</p>
</template>
<script>
export default {
  data: () => ({
    count: 0
  }),
  methods: {
    increaseCounter () {
      this.count += 1;
    }
  }
}
</script>
```

---
- Nova forma de criar componentes com Composition API:
```JS
<template>
  <p @click="increaseCounter">{{ state.count }}</p>
</template>
<script> import { reactive, ref } from 'vue';
 export default {
  setup(){
    const state = reactive({
      count: ref(0)
    });
 const increaseCounter = () => {
      state.count += 1;
    }
 return { state, increaseCounter }
  }
}
</script>
```

---

# 🤔 Atualização de Vue 2 para Vue 3

![bg](https://media1.tenor.com/images/24970688f48be4e47547dfa4421a276f/tenor.gif?itemid=4471517)

---

# Hora da Demo 😈

##### Quem quiser acompanhar
* Instalar cli estável do vue

`$ npm install -g @vue/cli` ou  `$ yarn global add @vue/cli`

* Criar projeto novo

`$ vue create demo-app-talk`

---

# Hora do Demo 😈

* Vamos escolher a opção com Vue3

![](https://dental-college.s3.amazonaws.com/presentations/demo-app-talk-1.png)

---

# Hora do Demo 😈

`$ cd demo-app-talk`
`$ yarn serve`

---

# Referências

- [Vue 3 live Release Evan You Creator Vuejs](https://www.youtube.com/watch?v=Vp5ANvd88x0)
- [Vue.js 3 Cookbook](https://www.packtpub.com/product/vue-js-3-cookbook/9781838826222)