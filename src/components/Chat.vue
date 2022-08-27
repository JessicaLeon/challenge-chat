<template>
  <div>
    <link
      rel="stylesheet"
      href="https://unpkg.com/tailwindcss@2.2.19/dist/tailwind.min.css"
    />
    <div class="">
      <!-- NavBar -->
      <nav class="h-1/4 flex-shrink-0 bg-blue-900">
        <div class="max-w-7xl mx-auto px-2 sm:px-4 lg:px-8">
          <div class="relative flex items-center justify-between h-16">
            <div
              class="text-white items-center justify-center text-center text-xl"
            >
              <h1>HEY CENTER</h1>
            </div>
            <div class="hidden lg:block lg:w-80">
              <div class="flex items-center justify-end">
                <div class="flex">
                  <a
                    href="#"
                    class="px-3 py-2 rounded-md text-sm font-medium text-white hover:text-white"
                  >
                    Mi cuenta
                  </a>
                </div>

                <div class="ml-4 relative flex-shrink-0">
                  <div>
                    <button
                      class="bg-red-700 flex text-sm rounded-full text-white focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-red-700 focus:ring-white"
                    >
                      <img
                        class="h-8 w-8 rounded-full"
                        src="@/assets/img/img03.jpg"
                      />
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </nav>
      <!-- Chat -->
      <section class="flex overflow-hidden">
        <!-- Chats Users -->
        <div class="bg-gray-50 w-3/12 p-6">
          <!-- Account Information -->
          <div class="overflow-auto">
            <div
              class="relative rounded-lg px-2 py-2 flex items-center space-x-3 hover:border-gray-400 mb-4"
            >
              <div class="flex-shrink-0">
                <img
                  class="h-12 w-12 rounded-full"
                  src="@/assets/img/img03.jpg"
                />
              </div>
              <div class="flex-1 min-w-0">
                <a href="#" class="focus:outline-none">
                  <span class="absolute inset-0" />
                  <p class="text-sm font-bold text-blue-900">Jessica León</p>
                  <p class="text-sm text-gray-500 truncate">
                    Ing. Software y Redes
                  </p>
                </a>
              </div>
            </div>
            <!-- Search -->
            <div class="mb-4">
              <div class="relative">
                <div
                  class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke-width="1.5"
                    stroke="currentColor"
                    class="w-5 h-5 text-gray-400"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z"
                    />
                  </svg>
                </div>
                <input
                  name="search"
                  class="focus:ring-red-500 focus:border-red-500 block w-full pl-10 sm-text-sm border-gray-100 rounded-full p-2 border"
                />
              </div>
            </div>
            <!-- User Component -->
            <user
              v-for="user in users"
              :key="user.userID"
              :user="user"
              :selected="selectedUser === user"
              @select="onSelectUser(user)"
            />
          </div>
        </div>
        <!-- MessagesPanel -->
        <div class="bg-white w-6/12">
          <message-panel
            v-if="selectedUser"
            :user="selectedUser"
            @input="onMessage"
          />
        </div>
        <!-- Profile -->
        <div class="bg-gray-50 w-3/12">
          <div
            class="pr-4 sm:pr-6 lg:pr-8 lg:flex-shrink-0 xl:pr-0 hidden xl:block"
          >
            <div class="h-full pl-6 py-6 lg:w-80">
              <div class="h-full relative">
                <div class="relative flex items-center justify-between pb-10">
                  <div class="flex font-bold text-gray-500">
                    <h1>09:30 AM</h1>
                  </div>
                  <div class="flex">
                    <div class="pr-2 text-gray-500">
                      <svg
                        xmlns="http://www.w3.org/2000/svg"
                        width="20"
                        height="20"
                        fill="currentColor"
                        class="bi bi-tag-fill"
                        viewBox="0 0 16 16"
                      >
                        <path
                          d="M2 1a1 1 0 0 0-1 1v4.586a1 1 0 0 0 .293.707l7 7a1 1 0 0 0 1.414 0l4.586-4.586a1 1 0 0 0 0-1.414l-7-7A1 1 0 0 0 6.586 1H2zm4 3.5a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0z"
                        />
                      </svg>
                    </div>
                    <div class="pr-2 text-gray-500">
                      <svg
                        xmlns="http://www.w3.org/2000/svg"
                        fill="none"
                        viewBox="0 0 24 24"
                        stroke-width="1.5"
                        stroke="currentColor"
                        class="w-5 h-5"
                      >
                        <path
                          stroke-linecap="round"
                          stroke-linejoin="round"
                          d="M18.364 18.364A9 9 0 005.636 5.636m12.728 12.728A9 9 0 015.636 5.636m12.728 12.728L5.636 5.636"
                        />
                      </svg>
                    </div>
                    <div class="text-gray-500">
                      <svg
                        xmlns="http://www.w3.org/2000/svg"
                        viewBox="0 0 24 24"
                        fill="currentColor"
                        class="w-5 h-5"
                      >
                        <path
                          d="M11.645 20.91l-.007-.003-.022-.012a15.247 15.247 0 01-.383-.218 25.18 25.18 0 01-4.244-3.17C4.688 15.36 2.25 12.174 2.25 8.25 2.25 5.322 4.714 3 7.688 3A5.5 5.5 0 0112 5.052 5.5 5.5 0 0116.313 3c2.973 0 5.437 2.322 5.437 5.25 0 3.925-2.438 7.111-4.739 9.256a25.175 25.175 0 01-4.244 3.17 15.247 15.247 0 01-.383.219l-.022.012-.007.004-.003.001a.752.752 0 01-.704 0l-.003-.001z"
                        />
                      </svg>
                    </div>
                  </div>
                </div>

                <div class="m-auto text-center mb-5">
                  <img
                    class="w-20 h-20 rounded-full m-auto"
                    src="@/assets/img/img03.jpg"
                  />
                  <h2 class="m-auto text-xl mt-2 text-blue-900">
                    Jessica León
                  </h2>
                  <h2 class="m-auto text-xs text-gray-500">5555555555</h2>
                </div>

                <div
                  class="mb-4 text-center text-sm font-bold text-blue-900 font-bold"
                >
                  <h4>Multimedia</h4>
                </div>
                <div class="mb-5 grid grid-cols-4 gap-2">
                  <div>
                    <div
                      class="cursor-pointer bg-gray-300 hover:bg-gray-400 h-14 w-full"
                    ></div>
                  </div>
                  <div>
                    <div
                      class="cursor-pointer bg-gray-300 hover:bg-gray-400 h-14 w-full"
                    ></div>
                  </div>
                  <div>
                    <div
                      class="cursor-pointer bg-gray-300 hover:bg-gray-400 h-14 w-full"
                    ></div>
                  </div>
                  <div>
                    <div
                      class="cursor-pointer bg-gray-300 hover:bg-gray-400 h-14 w-full"
                    ></div>
                  </div>
                  <div>
                    <div
                      class="cursor-pointer bg-gray-300 hover:bg-gray-400 h-14 w-full"
                    ></div>
                  </div>
                  <div>
                    <div
                      class="cursor-pointer bg-gray-300 hover:bg-gray-400 h-14 w-full"
                    ></div>
                  </div>
                  <div>
                    <div
                      class="cursor-pointer bg-gray-300 hover:bg-gray-400 h-14 w-full"
                    ></div>
                  </div>
                  <div>
                    <div
                      class="cursor-pointer bg-gray-300 hover:bg-gray-400 h-14 w-full"
                    ></div>
                  </div>
                </div>

                <div
                  class="mb-4 pt-4 text-center text-sm border-t-2 border-gray-20 text-gray-500"
                >
                  <h4>Marcar status de conversación como:</h4>
                </div>
                <div class="mb-2 text-center">
                  <button
                    class="inline-flex items-center justify-center rounded-full h-12 w-12 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300"
                  >
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24"
                      fill="currentColor"
                      class="w-4 h-4"
                    >
                      <path
                        fill-rule="evenodd"
                        d="M3.97 3.97a.75.75 0 011.06 0L12 10.94l6.97-6.97a.75.75 0 111.06 1.06L13.06 12l6.97 6.97a.75.75 0 11-1.06 1.06L12 13.06l-6.97 6.97a.75.75 0 01-1.06-1.06L10.94 12 3.97 5.03a.75.75 0 010-1.06z"
                        clip-rule="evenodd"
                      />
                    </svg>
                  </button>
                  <button
                    class="inline-flex items-center justify-center rounded-full h-12 w-12 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300"
                  >
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24"
                      fill="currentColor"
                      class="w-4 h-4"
                    >
                      <path
                        fill-rule="evenodd"
                        d="M21.545 3.627a.75.75 0 01-.03 1.06 47.349 47.349 0 00-11.04 15.89.75.75 0 01-1.22.238L2.47 14.03a.75.75 0 111.06-1.06l6.008 6.007A48.87 48.87 0 0120.484 3.598a.75.75 0 011.06.029z"
                        clip-rule="evenodd"
                      />
                    </svg>
                  </button>
                  <button
                    class="inline-flex items-center justify-center rounded-full h-12 w-12 transition duration-500 ease-in-out text-gray-500 hover:bg-gray-300"
                  >
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 24 24"
                      fill="currentColor"
                      class="w-4 h-4"
                    >
                      <path
                        fill-rule="evenodd"
                        d="M15.97 2.47a.75.75 0 011.06 0l4.5 4.5a.75.75 0 010 1.06l-4.5 4.5a.75.75 0 11-1.06-1.06l3.22-3.22H7.5a.75.75 0 010-1.5h11.69l-3.22-3.22a.75.75 0 010-1.06zm-7.94 9a.75.75 0 010 1.06l-3.22 3.22H16.5a.75.75 0 010 1.5H4.81l3.22 3.22a.75.75 0 11-1.06 1.06l-4.5-4.5a.75.75 0 010-1.06l4.5-4.5a.75.75 0 011.06 0z"
                        clip-rule="evenodd"
                      />
                    </svg>
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import socket from "../socket";
import User from "./User";
import MessagePanel from "./MessagePanel";

export default {
  name: "Chat",
  components: { User, MessagePanel },
  data() {
    return {
      selectedUser: null,
      users: [],
    };
  },
  methods: {
    onMessage(content) {
      if (this.selectedUser) {
        socket.emit("private message", {
          content,
          to: this.selectedUser.userID,
        });
        this.selectedUser.messages.push({
          content,
          fromSelf: true,
        });
      }
    },
    onSelectUser(user) {
      this.selectedUser = user;
      user.hasNewMessages = false;
    },
  },
  created() {
    socket.on("connect", () => {
      this.users.forEach((user) => {
        if (user.self) {
          user.connected = true;
        }
      });
    });

    socket.on("disconnect", () => {
      this.users.forEach((user) => {
        if (user.self) {
          user.connected = false;
        }
      });
    });

    const initReactiveProperties = (user) => {
      user.hasNewMessages = false;
    };

    socket.on("users", (users) => {
      users.forEach((user) => {
        user.messages.forEach((message) => {
          message.fromSelf = message.from === socket.userID;
        });
        for (let i = 0; i < this.users.length; i++) {
          const existingUser = this.users[i];
          if (existingUser.userID === user.userID) {
            existingUser.connected = user.connected;
            existingUser.messages = user.messages;
            return;
          }
        }
        user.self = user.userID === socket.userID;
        initReactiveProperties(user);
        this.users.push(user);
      });
      // put the current user first, and sort by username
      this.users.sort((a, b) => {
        if (a.self) return -1;
        if (b.self) return 1;
        if (a.username < b.username) return -1;
        return a.username > b.username ? 1 : 0;
      });
    });

    socket.on("user connected", (user) => {
      for (let i = 0; i < this.users.length; i++) {
        const existingUser = this.users[i];
        if (existingUser.userID === user.userID) {
          existingUser.connected = true;
          return;
        }
      }
      initReactiveProperties(user);
      this.users.push(user);
    });

    socket.on("user disconnected", (id) => {
      for (let i = 0; i < this.users.length; i++) {
        const user = this.users[i];
        if (user.userID === id) {
          user.connected = false;
          break;
        }
      }
    });

    socket.on("private message", ({ content, from, to }) => {
      for (let i = 0; i < this.users.length; i++) {
        const user = this.users[i];
        const fromSelf = socket.userID === from;
        if (user.userID === (fromSelf ? to : from)) {
          user.messages.push({
            content,
            fromSelf,
          });
          if (user !== this.selectedUser) {
            user.hasNewMessages = true;
          }
          break;
        }
      }
    });
  },
  destroyed() {
    socket.off("connect");
    socket.off("disconnect");
    socket.off("users");
    socket.off("user connected");
    socket.off("user disconnected");
    socket.off("private message");
  },
};
</script>

<style scoped></style>
