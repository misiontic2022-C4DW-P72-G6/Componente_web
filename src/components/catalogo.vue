<template>
  <div class="information">
      
    <div class="create-route">
      <h1>Nuestros Hoteles Asociados</h1>
    </div>

  
      <div class="cuadro_contenedor">
        <div class="create-route">
          Nombre:<br>
          <span>{{ catalogoDetailById.Nombre }}</span>
        </div>
        <br />

        <div class="create-route">
          Ubicación:
        <span>{{ catalogoDetailById.Ubicacion }}</span>
        </div>
        <br />

        <div class="create-route">
          Calificación:
        <span>{{ catalogoDetailById.Calificacion }}</span>
        </div>
        <br />

        <div class="create-route">
          Descripción:
        <span>{{ catalogoDetailById.Descripcion }}</span>
        </div>
        <br />

        <div class="create-route">
          Correo:
          <span>{{ catalogoDetailById.Correo }}</span>
        </div>
        <br />

        <nav>
        <button v-if="!is_auth" v-on:click="reservas">Reservar</button>
        </nav>
      </div>
        
      <div class="cuadro_contenedor">
        <div class="create-route">
          Nombre:
        <span>{{ catalogoDetailById.Nombre }}</span>
        </div>
        <br />

        <div class="create-route">
          Ubicación:
        <span>{{ catalogoDetailById.Ubicacion }}</span>
        </div>
        <br />

        <div class="create-route">
          Calificación:
        <span>{{ catalogoDetailById.Calificacion }}</span>
        </div>
        <br />

        <div class="create-route">
          Descripción:
          <span>{{ catalogoDetailById.Descripcion }}</span>
        </div>
        <br />

        <div class="create-route">
          Correo:
        <span>{{ catalogoDetailById.Correo }}</span>
        </div>
        <br />

        <nav>
        <button v-if="!is_auth" v-on:click="reservas">Reservar</button>
        </nav>
      </div>

      <div class="cuadro_contenedor">
        <div class="create-route">
          Nombre:
        <span>{{ catalogoDetailById.Nombre }}</span>
        </div>
        <br />

        <div class="create-route">
          Ubicación:
        <span>{{ catalogoDetailById.Ubicacion }}</span>
        </div>
        <br />

        <div class="create-route">
          Calificación:
        <span>{{ catalogoDetailById.Calificacion }}</span>
        </div>
        <br />

        <div class="create-route">
          Descripción:
        <span>{{ catalogoDetailById.Descripcion }}</span>
        </div>
        <br />

        <div class="create-route">
          Correo:
        <span>{{ catalogoDetailById.Correo }}</span>
        </div>
        <br />

        <nav>
        <button v-if="!is_auth" v-on:click="reservas">Reservar</button>
        </nav>
        <br>
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
      catalogoId: jwt_decode(localStorage.getItem("token_refresh")).catalogo_id, 
      
      catalogoDetailById: {
        Nombre: "",
        Correo: "",
      }
      /*catalogoId: 1,
      catalogoDetailById: {
        Nombre: "",
        Ubicacion: "",
        Calificacion: 0,
        Direccion: "",
        Descripcion: "",
        Correo: "",
        catalogoId: 2,
        catalogoDetailById: {
          Nombre: "",
          Ubicacion: "",
          Calificacion: 0,
          Direccion: "",
          Descripcion: "",
          Correo: "",
        },
      },*/
    };
  },
  apollo: {
    catalogoDetailById: {
      query: gql`
        query Query($catalogoId: Int!) {
          catalogoDetailById(catalogoId: $catalogoId) {
            Nombre
            Calificacion
            Ubicacion
            Direccion
            Descripcion
            Correo
          }
        }
      `,
      variables() {
        return {
          catalogoId: this.catalogoId,
        };
      },
    },
  },
};
</script>

<style>
.cuadro_contenedor {
  padding: 10px;
  margin-bottom: 10px;
  background-color: rgb(245, 245, 245);
  border: solid 1px red;
  display: grid;
  grid-template-columns: 33% 33% 33%;
  border-radius: 10px;
  box-shadow: 3px 3px 3px 2px rgba(197, 23, 23, 0.2);
  width: 50%;
  height: auto;
}
.create-route {
  border-radius: 5px;
  text-align: left;
  margin: 1px;
  padding: 0px;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}
.information {
  margin: 0;
  padding: 0%;
  width: 90%;
  height: 90%;
  display: flex;
  flex-direction: center;
  justify-content: center;
  align-items: center;
}
.information h1 {
  font-size: 60px;
  color: #283747;
}
.information h2 {
  font-size: 40px;
  color: #283747;
}
.information span {
  color: crimson;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}
.details h3 {
  font-size: 35px;
  color: #283747;
  text-align: center;
}
.details h2 {
  font-size: 35px;
  color: #283747;
}
.details {
  border: 3px solid #283747;
  border-radius: 10px;
  width: 80%;
  height: 80%;
  display: flex;
  flex-direction: column;
  justify-content: right;
  align-items: right;
}
</style>