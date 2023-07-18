<template>
  <div class="home">
    <h1>Home</h1>
    <!-- <p ref="para">My name is {{ name }} and my age is {{ age }}</p>
    <button @click="handleClick">Click Me</button>
    <button @click="age++">Add age</button>
    <input type="text" v-model="name" /> -->

    <!-- <h2>Refs</h2>
    <p>{{ ninjaOne.name }} - {{ ninjaOne.age }}</p>
    <button @click="updateNinjaOne">Update Ninja One</button>

    <h2>Reactive</h2>
    <p>{{ ninjaTwo.name }} - {{ ninjaTwo.age }}</p>
    <button @click="updateNinjaTwo">Update Ninja Two</button> -->

    <!-- <input type="text" v-model="search" />
    <p>search term - {{ search }}</p>
    <div v-for="name in matchingNames" :key="name">
      <h3>{{ name }}</h3>
    </div>
    <button @click="handleClick">Stop Watching</button> -->
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList v-if="showPosts" :posts="posts" />
    </div>
    <div v-else>Loading...</div>
    <button @click="showPosts = !showPosts">Toggle Posts</button>
    <button @click="posts.pop()">Delete Post</button>
  </div>
</template>

<script>
import PostList from "../components/PostList.vue";
import getPosts from "../composables/getPosts";
import { ref, reactive, computed, watch, watchEffect } from "vue";
export default {
  name: "HomeView",
  components: {
    PostList,
  },
  setup() {
    // ref lesson

    // const para = ref(null);

    // const name = ref("mario");
    // const age = ref(30);

    // const handleClick = () => {
    //   // console.log(para, para.value);
    //   // para.value.classList.add("test");
    //   // para.value.textContent = "hello world";
    //   name.value = "luigi";
    //   age.value = 35;
    // };

    //reactive lesson

    // const ninjaOne = ref({ name: "mario", age: 25 });
    // const ninjaTwo = reactive({ name: "yoshi", age: 40 });

    // const updateNinjaOne = () => {
    //   ninjaOne.value.name = "luigi";
    //   ninjaOne.value.age = 30;
    // };

    // const updateNinjaTwo = () => {
    //   ninjaTwo.name = "andre";
    //   ninjaTwo.age = 21;
    // };

    // const search = ref("");
    // const names = ref(["mario", "luigi", "yoshi"]);

    // const stopWatch = watch(search, () => {
    //   console.log("watch function ran");
    // });

    // const stopEffect = watchEffect(() => {
    //   console.log("watch effect ran", search.value);
    // });

    // const matchingNames = computed(() => {
    //   return names.value.filter((name) => {
    //     return name.includes(search.value);
    //   });
    // });

    // const handleClick = () => {
    //   stopWatch();
    //   stopEffect();
    // };

    // return { names, search, matchingNames, handleClick };

    const showPosts = ref(true);

    const { posts, error, load } = getPosts();

    load();

    return { posts, error, showPosts };
  },
};
</script>
