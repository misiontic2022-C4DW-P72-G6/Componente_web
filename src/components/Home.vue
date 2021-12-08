<template>
  <div class="information">
    <h1>
      ¡Bienvenido
      <span>{{ userDetailById.name }}</span
      >!
    </h1>
    <div class="details">
      <h3>Gracias por confiar en nosotros...</h3>
      <h2>
        Hola!
        <span>{{userDetailById.Nombres }}</span>
      </h2>
      <h2>
        Correo electrónico:
        <span>{{userDetailById.Correo }}</span>
      </h2>
    </div>
  </div>
</template>

<script>
import gql from "graphql-tag";
import jwt_decode from "jwt-decode";
export default {
  name: "Home",
  data: function () {
    return {
      userId: jwt_decode(localStorage.getItem("token_refresh")).user_id,
      userDetailById: {
        Nombres: "",
        Correo: "",
        
      },
    };
  },
  apollo: {
    userDetailById: {
      query: gql`
        query ($userId: Int!) {
          userDetailById(userId: $userId) {
            Nombres
            Correo
            
          }
        }
      `,
      variables() {
        return {
          userId: this.userId,
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
  height: 90%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.information h1 {
  height: 5%;
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
  padding: 30px 4px;
  margin: 10px 0 0 0;
}
</style>