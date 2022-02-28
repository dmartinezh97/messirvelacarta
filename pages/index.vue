<template>
  <div>
    <div class="fixed top-0 w-full mb-2 border-b color-fondo border-gray-700 z-20">
        <ul class="flex flex-wrap justify-around -mb-px" id="myTab" data-tabs-toggle="#myTabContent" role="tablist">
            <li v-for="(categoria, index) in datos" :key="'categoria-'+categoria.name" class="mr-2">
                <button @click="onClickCategoria" :id="`${categoria.name}-tab`" :data-tabs-target="`${categoria.name}`" type="button" role="tab" :class="index == 0 ? 'active' : ''" class="inline-block capitalize py-4 px-4 text-sm font-medium text-center text-gray-500 rounded-t-lg border-b-2 border-transparent hover:text-gray-600 hover:border-gray-300 dark:text-gray-400 dark:hover:text-gray-300">{{categoria.name}}</button>
            </li>
            <!-- <li class="mr-2" role="presentation">
                <button @click="onClickCategoria" id="dashboard-tab" data-tabs-target="dashboard" type="button" role="tab" class="inline-block py-4 px-4 text-sm font-medium text-center text-gray-500 rounded-t-lg border-b-2 border-transparent hover:text-gray-600 hover:border-gray-300 dark:text-gray-400 dark:hover:text-gray-300">Dashboard</button>
            </li> -->
        </ul>
    </div>
    <div id="myTabContent" class="mt-14 z-10">
        <div v-for="(categoria, index) in datos" :class="index != 0 ? 'hidden' : ''" :key="'categoria-tab-'+categoria.name" class="grid grid-cols-2 gap-4 p-4" :id="categoria.name" role="tabpanel">
            <div v-for="producto in categoria.productos" :key="producto.name" class="flex flex-col">
                    <div class="relative overflow-hidden rounded-xl shadow-lg">
                      <img class="object-cover w-full h-48" :src="`/img/${producto.img}`" alt="">
                      <span class="absolute bottom-2 right-2 border border-gray-400 text-sm font-medium px-2.5 py-0.5 rounded bg-gray-700 text-gray-300">{{producto.precio}} €</span>
                    </div>
                    <div class="flex flex-col justify-between py-2">
                      <div>
                        <p class="text-base font-medium text-gray-200"> {{producto.name}} </p>
                        <p class="text-base text-gray-400 leading-tight" v-html="producto.description"></p>
                      </div>
                      <!-- <div class="flex items-center mt-6">
                        <div class="flex-shrink-0">
                          <a href="https://twitter.com/Mike_Andreuzza">
                            <span class="sr-only">Michael Andreuzza</span>
                            <img class="w-10 h-10 rounded-full" src="https://d33wubrfki0l68.cloudfront.net/2f76102fd18a4e095eaed7a836a3f2183a982a4d/91dd4/images/avatar.jpg" alt="">
                          </a>
                        </div>
                        <div class="ml-3">
                          <p class="text-sm font-medium text-neutral-600">
                            <a href="https://twitter.com/Mike_Andreuzza" class="hover:underline"> Michaerl Andreuzza</a>
                          </p>
                          <div class="flex space-x-1 text-sm text-gray-500">
                            <time datetime="2020-03-16"> Mar 16, 2020 </time>
                            <span aria-hidden="true"> · </span>
                            <span> 6 min read </span>
                          </div>
                        </div>
                      </div> -->
                    </div>
                  </div>
            <!-- <pre class="font-medium text-gray-800 dark:text-white">
              {{categoria}}
            </pre> -->
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  head(){
    return {
      title: 'Messirvelacarta - Inicio'
    }
  },
  data() {
    return {
      datos: [
        {
          'id': 'refrescos',
          'name': 'Refrescos',
          'productos': [
            {
              'name': 'Coca Cola',
              'description': '- Zero',
              'precio': '2,50',
              'img': 'cocacola.jpg'
            },
            {
              'name': 'Nestea',
              'description': '- Limón',
              'precio': '2,50',
              'img': 'nestea.jpg'
            },
            {
              'name': 'Red Bull',
              'description': '- Zero<br>- Coco<br>- Sandía<br>- Arándanos<br>- Açaí',
              'precio': '2,50',
              'img': 'redbull.jpg'
            },
          ]
        },
        {
          'id': 'shishas',
          'name': 'Shishas',
          'productos': [
            {
              'name': 'Love 66',
              'description': 'Maracuya / fruta de la pasión, Melón, Menta y Sandia.',
              'precio': '12,5',
              'img': 'love66.jpg'
            },
            {
              'name': 'Hawaii',
              'description': 'Piña, Mango y Menta',
              'precio': '12,5',
              'img': 'hawaii.jpg'
            },
            {
              'name': 'Lady Killer',
              'description': 'Frutos del bosque, Mango, Melón, Menta',
              'precio': '12,5',
              'img': 'ladykiller.jpg'
            },
          ]
        },
        {
          'id': 'cocteles',
          'name': 'Cocteles',
          'productos': [
            {
              'name': 'Coca Cola',
              'description': '- Zero',
              'precio': '2,50',
              'img': 'cocacola.jpg'
            },
            {
              'name': 'Nestea',
              'description': '- Limón',
              'precio': '2,50',
              'img': 'nestea.jpg'
            },
            {
              'name': 'Red Bull',
              'description': '- Zero<br>- Coco<br>- Sandía<br>- Arándanos<br>- Açaí',
              'precio': '2,50',
              'img': 'redbull.jpg'
            },
          ]
        },
      ]
    }
  },
  methods:{
    onClickCategoria(e){
      var id = e.currentTarget.getAttribute('data-tabs-target');
      var tab = document.getElementById(id);
      if(tab!=null){
        this.disableAllTabs();
        e.currentTarget.classList.add('active')
        this.disableAllContentTabs();
        tab.classList.remove('hidden')
      }
    },
    disableAllTabs(){
      document.querySelectorAll('[role="tab"]').forEach(x => x.classList.remove('active'))
    },
    disableAllContentTabs(){
      document.querySelectorAll('[role="tabpanel"]').forEach(x => x.classList.add('hidden'))
    }
  }
}
</script>

<style scoped>
[role="tab"].active {
    @apply text-red-600 border-red-600 dark:text-red-500 dark:border-red-500 hover:text-red-600 hover:border-red-600 dark:hover:text-red-500 dark:hover:border-red-500;
}
</style>