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
              <v-btn color="primary" @click="showAddProfessorDialog = true"
                >Adicionar Turmas</v-btn
              >

              <v-table fixed-header height="500px">
                <thead>
                  <tr>
                    <th class="text-left">Name</th>
                    <th class="text-left">Actions</th>
                  </tr>
                </thead>
                <tbody>
                  <tr v-for="turma in classes" :key="turma.id">
                    <td>{{ turma.name }}</td>
                    <td>
                      <div class="d-flex">
                        <v-btn>
                          <v-icon color="error" @click="removeTurma(turma)"
                            >mdi-delete</v-icon
                          >
                        </v-btn>
                        <v-btn>
                          <v-icon @click="updateTurma = true"
                            >mdi-pencil</v-icon
                          >
                        </v-btn>
                        <v-btn>
                          <ModalClasses />
                        </v-btn>
                      </div>
                    </td>
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

const cards = ref(["Turmas"])
const drawer = ref(null)
const links = ref([
  ["mdi-account-circle", "Professores"],
  ["mdi-school", "Conteúdos"],
])

const classes = ref([
  { id: 1, name: "5° N3" },
  { id: 2, name: "5° V5" },
  { id: 3, name: "15° M3" },
])
</script>
