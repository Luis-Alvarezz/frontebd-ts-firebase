<template>
  <v-card width="1200" class="mx-auto">
    <v-card-title>
      Registra tu cuenta
    </v-card-title>

    <v-card-text>
      <v-row>
        <v-col cols="4">
          <v-text-field
            v-model="user.nombre"
            label="Nombre"
            placeholder="Tu nombre"
            outlined
          />
        </v-col>

        <v-col cols="4">
          <v-text-field
            v-model="user.apaterno"
            label="Apellido Paterno"
            placeholder="Ingresa tu apellido paterno"
            outlined
          />
        </v-col>

        <v-col cols="4">
          <v-text-field
            v-model="user.amaterno"
            label="Apellido Materno"
            placeholder="Ingresa tu apellido materno"
            outlined
          />
        </v-col>

        <v-row>
          <v-col cols="6">
            <v-text-field
              v-model="user.direccion"
              label="Dirección"
              placeholder="Ingresa el lugar donde vives"
              outlined
            />
          </v-col>

          <v-col cols="6">
            <v-text-field
              v-model="user.telefono"
              label="Telefono"
              placeholder="Sin espacios"
              outlined
            />
          </v-col>
        </v-row>

        <v-row>
          <v-col cols="4">
            <v-text-field
              v-model="user.ciudad"
              label="Tu Ciudad"
              placeholder="Ingresa el valor"
              outlined
            />
          </v-col>

          <v-col cols="4">
            <v-text-field
              v-model="user.estado"
              label="Tu Estado"
              placeholder="Ingresa el valor Completo"
              outlined
            />
          </v-col>
        </v-row>

        <v-col cols="6">
          <v-text-field
            v-model="user.usuario"
            label="Usuario"
            placeholder="Crea tu usuario"
            outlined
          />
        </v-col>

        <v-col cols="6">
          <v-text-field
            v-model="user.password"
            label="Password"
            placeholder="Ingresa una contraseña mayor a 6 carácteres"
            outlined
          />
        </v-col>
      </v-row>
    </v-card-text>

    <v-card-actions>
      <b-btn color="primary" @click="register">
        Registrarse
      </b-btn>

      <v-btn color="secondary" to="/">
        Regresar
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  data () {
    return {
      user: {
        nombre: '',
        apaterno: '',
        amaterno: '',
        direccion: '',
        telefono: '',
        ciudad: '',
        estado: '',
        usuario: '',
        password: ''
      }
    }
  },
  methods: {
    async register () {
      const response = await this.$axios.post('/users/create', this.user)
      // console.log(response)
      if (response && response.data && response.dara.id) {
        this.$store.commit('alert/setAlert', {
          message: 'Usuario registrado correctamente',
          type: 'success'
        })
        this.$store.push('/')
      }
    }
  }
}
</script>

<style scoped>
</style>
