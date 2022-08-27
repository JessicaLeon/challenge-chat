<template>
  <div>
    <link
      rel="stylesheet"
      href="https://unpkg.com/tailwindcss@2.2.19/dist/tailwind.min.css"
    />
    <div class="flex-grow w-full max-w-7xl mx-auto lg:flex">
      <div class="flex-1 min-w-0 bg-white xl:flex">
        <!-- ChatPersonContent -->
        <div
          class="flex-1 p:2 sm:pb-6 justify-between h-screen flex flex-col hidden xl:flex"
        >
          <div class="px-10 py-4 border-b">
            <div class="flex">
              <div class="relative w-12 mr-4">
                <img
                  src="@/assets/img/img03.jpg"
                  class="rounded-full w-12 h-12"
                />
              </div>
              <div class="self-center">
                <p class="font-medium">{{ user.username }}</p>
                <small class="text-gray-500">{{ status }}</small>
              </div>
            </div>
          </div>
          <!-- MessagesPanel -->
          <div
            id="messages"
            class="flex flex-col space-y-4 p-3 overflow-y-auto scrollbar-thumb-blue scrollbar-thumb-rounded scrollbar-track-blue-lighter scrollbar-w-2 scrolling-touch"
          >
            <div v-for="(message, index) in user.messages" :key="index">
              <!-- first message -->
              <div class="chat-message" v-if="message.fromSelf">
                <div class="flex items-end justify-end">
                  <div
                    class="flex flex-col space-y-2 text-xs max-w-xs mx-2 order-2 items-end"
                  >
                    <div class="relative flex">
                      <div
                        class="px-4 py-2 rounded-lg flex rounded-bl-none bg-blue-900 text-white text-sm"
                        :key="index"
                      >
                        {{ message.content }}
                        <div></div>
                      </div>
                    </div>
                    <small class="text-gray-500">02:07 p.m</small>
                  </div>
                </div>
              </div>
              <!-- second message -->
              <div class="chat-message" v-else>
                <div class="flex items-end">
                  <div
                    class="flex flex-col space-y-2 text-xs max-w-xs mx-2 order-2 items-start"
                  >
                    <div>
                      <span
                        class="px-4 py-2 rounded-lg inline-block rounded-bl-none bg-gray-200 text-gray-600"
                        :key="index"
                      >
                        {{ message.content }}
                      </span>
                    </div>
                    <small class="text-gray-500">02:07 p.m</small>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <!-- InputMessage -->
          <div class="py-3 px-5 flex border-t">
            <input
              type="text"
              v-model="input"
              class="px-4 py-2 bg-gray-100 w-full focus:outline-none rounded-md"
              placeholder="Escribe un mensaje..."
            />
            <button>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="w-6 mr-4 text-gray-500"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M18.375 12.739l-7.693 7.693a4.5 4.5 0 01-6.364-6.364l10.94-10.94A3 3 0 1119.5 7.372L8.552 18.32m.009-.01l-.01.01m5.699-9.941l-7.81 7.81a1.5 1.5 0 002.112 2.13"
                />
              </svg>
            </button>
            <button>
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="w-6 mr-4 text-gray-500"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  d="M15.182 15.182a4.5 4.5 0 01-6.364 0M21 12a9 9 0 11-18 0 9 9 0 0118 0zM9.75 9.75c0 .414-.168.75-.375.75S9 10.164 9 9.75 9.168 9 9.375 9s.375.336.375.75zm-.375 0h.008v.015h-.008V9.75zm5.625 0c0 .414-.168.75-.375.75s-.375-.336-.375-.75.168-.75.375-.75.375.336.375.75zm-.375 0h.008v.015h-.008V9.75z"
                />
              </svg>
            </button>
            <button
              :disabled="!isValid"
              class="text-gray-500"
              @click="onSubmit"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                viewBox="0 0 24 24"
                fill="currentColor"
                class="w-6 h-6"
              >
                <path
                  d="M3.478 2.405a.75.75 0 00-.926.94l2.432 7.905H13.5a.75.75 0 010 1.5H4.984l-2.432 7.905a.75.75 0 00.926.94 60.519 60.519 0 0018.445-8.986.75.75 0 000-1.218A60.517 60.517 0 003.478 2.405z"
                />
              </svg>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MessagePanel",
  components: {},
  props: {
    user: Object,
    selected: Boolean,
  },
  data() {
    return {
      input: "",
    };
  },
  methods: {
    onSubmit() {
      this.$emit("input", this.input);
      this.input = "";
    },
    displaySender(message, index) {
      return (
        index === 0 ||
        this.user.messages[index - 1].fromSelf !==
          this.user.messages[index].fromSelf
      );
    },
  },
  computed: {
    isValid() {
      return this.input.length > 0;
    },
    status() {
      return this.user.connected ? "En línea" : "Desconectado";
    },
  },
};
</script>

<style scoped>
.header {
  line-height: 40px;
  padding: 10px 20px;
  border-bottom: 1px solid #dddddd;
}

.messages {
  margin: 0;
  padding: 20px;
}

.message {
  list-style: none;
}

.sender {
  font-weight: bold;
  margin-top: 5px;
}

.form {
  padding: 10px;
}

.input {
  width: 80%;
  resize: none;
  padding: 10px;
  line-height: 1.5;
  border-radius: 5px;
  border: 1px solid #000;
}

.send-button {
  vertical-align: top;
}
</style>
