<template>
  <div>
    <link
      rel="stylesheet"
      href="https://unpkg.com/tailwindcss@2.2.19/dist/tailwind.min.css"
    />
    <div class="h-full pl-4 pr-2 py-2 sm:pl-6 lg:pl-8 xl:pl-1">
      <div class="h-full relative">
        <!-- BoxUser -->
        <div
          class="relative rounded-lg px-2 py-2 flex items-center space-x-3 hover:border-gray-400 focus-within:ring-2 mb-3 hover:bg-gray-200"
          @click="onClick"
          :class="{ selected: selected }"
        >
          <div class="flex-shrink-0">
            <img class="h-10 w-10 rounded-full" src="@/assets/img/img03.jpg" />
          </div>
          <div class="flex-1 min-w-0">
            <a href="#" class="focus:outline-none">
              <div class="flex items-center justify-between">
                <p class="text-sm font-bold text-blue-900">
                  {{ user.username }} {{ user.self ? " (Tú)" : "" }}
                </p>
                <small class="flex-grow pl-2"
                  ><status-icon :connected="user.connected"
                /></small>
                <div class="text-gray-400 text-xs">12:35 AM</div>
              </div>
              <div class="flex items-center justify-between">
                <p class="text-sm text-gray-500 truncate">
                  {{ lastMessages(user).pop() }}
                </p>
                <div
                  class="text-white text-xs bg-red-600 rounded-full px-1 py-0"
                  v-if="user.hasNewMessages"
                >
                  1
                </div>
              </div>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import StatusIcon from "./StatusIcon";
export default {
  name: "User",
  components: { StatusIcon },
  props: {
    user: Object,
    selected: Boolean,
  },
  methods: {
    onClick() {
      this.$emit("select");
    },
    lastMessages(user) {
      return user.messages.map((a) => a.content);
    },
  },
  computed: {
    status() {
      return this.user.connected ? "En línea" : "Desconectado";
    },
  },
};
</script>

<style scoped>
.user {
  padding: 10px;
}

.description {
  display: inline-block;
}

.status {
  color: #92959e;
}

.new-messages {
  color: white;
  background-color: red;
  width: 20px;
  border-radius: 5px;
  text-align: center;
  float: right;
  margin-top: 10px;
}
</style>
