# 📗 Clase 13 Directivas:

Las directivas nos atributos que Vuejs utiliza para renderizar y generar reactividad en el DOM según de modifiquen los valores asociados.

## v-show:

La directiva v-show, muestra o oculta el elemento en HTML según un valor boleado de verdadero o falso.

```html
<p v-show="false">Mostrar Parrafo</p>
```

## v-if:

La directiva `v-if` nos va a permitir modificar el renderizado de elementos dentro de nuestro DOM en base a unas condiciones. Por ejemplo:

```html
<p v-if="0 < 5">Mostrar parrafo v-if</p>
<p v-else>Mostrar parrafo v-else</p>
```

## v-for:

La directiva `v-for` nos permite renderizar arrays o colecciones. Su sintaxis es muy sencilla y podemos aplicarla directamente en el **elemento** que queramos repetir o aplicar el blucle.

Por ejemplo, imagina que tenemos el Array siguiente:

```js
items: [1,2,3,4,5]
```

Una manera de recorrer ese array y renderizarlo en el DOM seria:

```html
<ul>
  <li v-for="item in items">{{ item }}</li>
</ul>
```

## v-model:

Esta directiva nos perminte asociar una entrada por parte del usuario, con nuetro modelo de datos.

`<input v-model="name" />`

Para poder bindear el input con nuestro modelo, debemos crear una propiedad con el nombre que asociaeremos a la propiedad `v-model`, en este caso **name**.


```js
data() {
  return {
    name: ''
  }
}
```

## v-on:

La directiva `v-on` nos permite "escuchar" eventos que ocurran dentro nuestro DOM.Como por ejemplo el evento `click` en un botón.
Por ejemplo:

```html 
<button v-on:click="pulsado">Pulsa</button>
```

Para poder procesar el evento click del boton, debemos crear un metodo dentro de nuestro componente:

```js
methods: {
  pulsado() {
    console.log("Botón pulsado")
  }
}
```

### 📚 Referencias y ayudas

- [Renderizado de listas v-for](https://es.vuejs.org/v2/guide/list.html)
- [Renderizado condicional](https://es.vuejs.org/v2/guide/conditional.html)
- [Directivas en vuejs](https://es.vuejs.org/v2/guide/syntax.html#Directivas)
- [Bulma io](https://bulma.io/)
- [Single File Components](https://vuejs.org/v2/guide/single-file-components.html)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [GitHub](https://github.com/)
