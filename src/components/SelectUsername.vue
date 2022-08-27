<template>
  <div>
    <link
      rel="stylesheet"
      href="https://unpkg.com/tailwindcss@2.2.19/dist/tailwind.min.css"
    />
    <div
      class="min-h-screen bg-gray-100 text-gray-800 antialiased px-4 py-6 flex flex-col justify-center sm:py-12"
    >
      <div class="relative py-3 sm:max-w-xl mx-auto text-center">
        <span class="text-2xl font-light">SELLIA CHAT</span>
        <div class="relative mt-4 bg-white shadow-md sm:rounded-lg text-left">
          <div class="h-2 bg-blue-900 rounded-t-md"></div>
          <div class="py-6 px-8">
            <span class="block font-semibold">Usuario</span>
            <input
              v-model="username"
              type="text"
              placeholder="Ingresa tu usuario"
              class="border w-full h-5 px-3 py-5 mt-2 hover:outline-none focus:outline-none focus:ring-1 focus:ring-indigo-600 rounded-md"
            />
            <div class="flex justify-center items-baseline">
              <button
                class="mt-4 bg-blue-900 text-white py-2 px-6 rounded-lg"
                @click="onSubmit"
              >
                Login
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SelectUsername",
  data() {
    return {
      username: "",
    };
  },
  computed: {
    isValid() {
      return this.username.length > 2;
    },
  },
  methods: {
    onSubmit() {
      this.$emit("input", this.username);
    },
  },
};
</script>

<style scoped>
.select-username {
  width: 300px;
  margin: 200px auto 0;
}
</style>
