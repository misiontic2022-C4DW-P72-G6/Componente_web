<template>
  <template>
  <div class="information">
    <h1>
      ¡Catalogo Hoteles
      <span>{{ catalogoDetailById.nombre }}</span
      >!
    </h1>
    <div class="details">
      <h3>La informacion para el Hotel es la siguiente</h3>
      <h2>
        Nombre del Hotel:
        <span>{{ catalogoDetailById.Nombre }}</span>
      </h2>
      <h2>
        Ubicacion:
        <span>{{ catalogoDetailById.Ubicacion }}</span>
      </h2>
      <h2>
        Calificacion:
        <span>{{ catalogoDetailById.Calificacion }}</span>
      </h2>
      <h2>
        Direccion:
        <span>{{ catalogoDetailById.Direccion }}</span>
      </h2>
      <h2>
        Descripcion:
        <span>{{ catalogoDetailById.Descripcion }}</span>
      </h2>
      <h2>
        Correo electrónico:
        <span>{{ catalogoDetailById.Correo }}</span>
      </h2>
      <h2>

    </div>
  </div>
</template>

<script>
import gql from "graphql-tag";
import jwt_decode from "jwt-decode";
export default {
  name: "catalogo",
  data: function () {
    return {
      idHotel: jwt_decode(localStorage.getItem("token_refresh")).idHotel,
      catalogoDetailById: {
        Nombre: "",
        Ubicacion: "",
        Calificacion: "",
        Descripcion: "",
        Correo: "",
      },
    };
  },
  apollo: {
    catalogoDetailById: {
      query: gql`
        query ($idHotel: Int!) {
          catalogoDetailById(userId: $idHotel) {
            Nombre
            Ubicacion
            Calificacion
            Descripcion
            Correo
          }
        }
      `,
      variables() {
        return {
          idHotel: this.idHotel,
        };
      },
    },
  },
};