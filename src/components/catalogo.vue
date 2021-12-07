<template>
  <div class="information">
    <h1>
      ¡Catalogo
      <span>{{ catalogoDetailById.catalogoId }}</span
      >!
    </h1>
    <div class="details">
      <h3>Hotel </h3>

        <h2>
        Nombre:
        <span>{{ catalogoDetailById.Nombre }}</span>
        </h2>
      
        <h2>
        Ubicacion:
        <span>{{ catalogoDetailById.Ubicacion }}</span>
        </h2>  

        <h2>
        Calificación:
        <span>{{ catalogoDetailById.Calificacion }}</span>
        </h2>
        
       <h2>   
        Descripción:
        <span>{{ catalogoDetailById.Descripcion }}</span>
        </h2>  
      
         <h2>  
        Correo:
        <span>{{ catalogoDetailById.Correo }}</span>
        </h2>  

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
      catalogoId: jwt_decode(localStorage.getItem("token_refresh")).catalogo_Id,
      catalogoDetailById: {
        Nombre: "",
        Ubicacion: "",
        Calificacion: 0,
        Direccion: "",
        Descripcion: "",
        Correo: "",
        
        
      },
    };
  },
  apollo: {
    catalogoDetailById: {
      query: gql`
        query ($catalogoId: Int!) {
          catalogoDetailById(catalogoId: $catalogoId) {
            Nombre
            Ubicacion
            Calificacion
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
.information {
  margin: 0;
  padding: 0%;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
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
  font-weight: bold;
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
  border: 3px solid rgba(0, 0, 0, 0.3);
  border-radius: 20px;
  padding: 30px 80px;
  margin: 30px 0 0 0;
}
</style>