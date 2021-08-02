<template>
  <div>
    <div
      v-for="todo in todoList"
      :key="todo.id"
      class="max-w-md mx-auto py-4 px-8 shadow-lg rounded-lg my-20"
      :class="{ completed: todo.completed, 'un-completed': todo.completed == false }"
    >
      <div class="flex justify-center md:justify-end -mt-16">
        <img
          class="w-20 h-20 object-cover rounded-full border-2 border-indigo-500"
          src="https://images.unsplash.com/photo-1499714608240-22fc6ad53fb2?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=334&q=80"
        />
      </div>
      <div>
        <h2 class="text-gray-800 text-3xl font-semibold">{{ todo.title }}</h2>
        <p class="mt-2 text-gray-600">
          {{ todo.comments }}
        </p>
      </div>
      <div class="flex justify-between mt-4">
        <div>
          <input type="checkbox" class="form-check-input" v-model="todo.completed" :id="'v_completed_' + todo.id" />
          <label class="form-check-label" :for="'v_completed_' + todo.id">Tamamlandı!</label>
        </div>
        <a :href="`/${todo.author}`" class="text-xl font-medium text-indigo-500">{{ todo.author }}</a>
      </div>
      <button v-if="todo.completed === true" @click="removeTodo(todo)" class="bg-red-600 pl-1 pr-1 text-white rounded-md mt-0 text-lg">
        Remove TODO
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todoList: [
        {
          id: 1,
          title: 'Dişlerini Fırçala',
          comments: 'Diş temizliğim ve çürükleri önlemek amacıyla kendi dişlerimi temizlemem gerekiyor.',
          author: 'Berkant',
          completed: false,
        },
        {
          id: 2,
          title: 'Yazılım çalış',
          comments: 'Geleceğin en popüler iş modülü olduğundan mütevellit öğrenmem gerek.',
          author: 'Berkay',
          completed: false,
        },
        {
          id: 3,
          title: 'Tailwind Öğren',
          comments:
            'Bootstrap yetersiz kaldığını düşünerek Tailwind öğrenmek daha güzel uilar ve web tasarımları ortaya çıkartmak için ya Tailwind ya da WindiCss öğrenmem gerek.',
          author: 'Mert',
          completed: false,
        },
        {
          id: 4,
          title: 'E-Ticaret işini hallet',
          comments:
            'E-Ticaret işi günümüzde popülasyonu yüksek seviyelere gelmiş artık iş modeli haline dönüşmüş şekilde bir iştir. Para kazanmak için bir iş modelidir.',
          author: 'Melikşah',
          completed: false,
        },
        {
          id: 5,
          title: 'Javascript Öğren',
          comments:
            "Ah üzümlü kekim canım Javascript'im benim artık günümüzde bir çok şeyi javascript ile yapmak mümkün olduğundan dolayı her yazılımcının öğrenmesi gereken bir dil olduğunu düşünüyorum. Javascript çok önemlidir benim için.",
          author: 'Hasibe',
          completed: false,
        },
      ],
    }
  },
  methods: {
    removeTodo(todos) {
      this.todoList = this.todoList.filter((todo) => todo !== todos)
    },
  },
}
</script>

<style>
.un-completed {
  @apply bg-red-300 text-black;
}
.completed {
  @apply bg-green-400 text-black;
}
</style>
