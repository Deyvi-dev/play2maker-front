<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer">
      <v-sheet color="grey-lighten-4" class="pa-4">
        <v-avatar class="mb-4" color="grey-darken-1" size="64"></v-avatar>

        <div>john@google.com</div>
      </v-sheet>

      <v-divider></v-divider>

      <v-list>
        <v-list-item v-for="[icon, text] in links" :key="icon" link>
          <template v-slot:prepend>
            <v-icon>{{ icon }}</v-icon>
          </template>

          <v-list-item-title>{{ text }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-main>
      <v-container class="py-8 px-6" fluid>
        <v-row>
          <v-col v-for="card in cards" :key="card" cols="12">
            <v-card>
              <v-card-title> {{ card }} </v-card-title>

              <v-btn @click="showAddProfessorDialog = true"
                >Adicionar Professor</v-btn
              >
              <v-table fixed-header height="500px">
                <thead>
                  <tr>
                    <th class="text-left">Name</th>
                    <th class="text-left">email</th>
                    <th></th>
                  </tr>
                </thead>
                <tbody>
                  <tr v-for="professor in professors" :key="professor.id">
                    <td>{{ professor.name }}</td>
                    <td>{{ professor.email }}</td>
                    <td>
                      <!-- <v-btn @click="editProfessor(professor)">Editar</v-btn> -->
                      <ModalProfile />
                    </td>
                    <!-- <td>
                      <v-btn
                        color="error"
                        outlined
                        rounded
                        @click="removeProfessor(professor)"
                      >
                        Remover
                      </v-btn>
                    </td> -->
                  </tr>
                </tbody>
              </v-table>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from "vue"

const cards = ref(["Professores"])
const drawer = ref(null)
const links = ref([
  ["mdi-account-circle", "Professores"],
  ["mdi-school", "Conteúdos"],
])

const professors = ref([
  { id: 1, name: "John Doe", email: "johndoe@example.com" },
  { id: 2, name: "Jane Doe", email: "janedoe@example.com" },
  { id: 3, name: "Bob Smith", email: "bobsmith@example.com" },
])
</script>
