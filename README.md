# 📗 Clase 40 Borrando documentos en Firebase(firestore)

## Método `deleteDocument()`

Para borrar un documento en firebase, primero debemos crear una referencia al documento, de igual manera que hicimos en la clase anterior al actualizar. en este caso usamos el método delete().

```js
deleteDocument(id) {
  const ref = db.collection('restaurants').doc(id)
  ref.delete()
}
```

### ⚒️ RECOMENDACIÓN:

### 📚 Referencias y ayudas
- [Firebase](https://firebase.google.com/docs/projects/learn-more?hl=es)
- [Guía Oficial de Nuxtjs](https://nuxtjs.org/guide)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)