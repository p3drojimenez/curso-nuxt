# 📗 Clase 44 Reto

Ya estamos apunto de pasar nuestra aplicación a producción y por lo tanto queremos hacer uso del sistema de firebase que hemos configurado. 

El reto consiste en transformar nuestros componentes y páginas para que dejen de usar un sistema de llamadas a la API y usen Firebase.

Para ello, ayudate de los ejemplos de las últimas clases.

- Primero, te recomiendo que te crees en la base de datos de firebase unos cuantos perfiles de restaurantes para que dispongas de datos suficientes para pruebas.

- Te encontrarás con un pequeño inconveniente a la hora de realizar una consulta a firebase para filtrar solo los restaurantes de una categoria en concreto, pero te dejo una pequeña pista de la [documentación oficial de firebase](https://firebase.google.com/docs/firestore/query-data/queries?hl=es)

  ```js
  let citiesRef = db.collection('cities');
  let query = citiesRef.where('capital', '==', true).get()
    .then(snapshot => {
      if (snapshot.empty) {
        console.log('No matching documents.');
        return;
      }

      snapshot.forEach(doc => {
        console.log(doc.id, '=>', doc.data());
      });
    })
    .catch(err => {
      console.log('Error getting documents', err);
    });
  ```

## SuperReto!

Si aun tienes ganas de más, nuestra aplicación tiene la funcionalidad de sumar likes a los restaurantes, pero hasta ahora, no haciamos nada con ellos. Sería interesante que se pudiesen contabilidad los likes y asi tenerlos de una manera persistida en la base de datos de firebase.

### ⚒️ RECOMENDACIÓN:

### 📚 Referencias y ayudas
- [Firebase](https://firebase.google.com/docs/projects/learn-more?hl=es)
- [Middlewares](https://nuxtjs.org/api/pages-middleware/)
- [Guía Oficial de Nuxtjs](https://nuxtjs.org/guide)