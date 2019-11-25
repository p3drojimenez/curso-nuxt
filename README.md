# 📗 Clase 33 Test Unitarios:

Los test unitarios nos van a permitir comprobar que nuestros componentes, páginas y funciones y comprobar que funcionan siempre de la manera esperada, de manera que si hacemos alguna modificación en alguna parte del código podramos ver **qué** ha fallado y **donde**.

Hay multitud de tipos de tests y cada uno enfocado a testear un momento o proceso en el desarrollo del software. Nostros realizamos los **test unitarios**, que nos permitirán realizar pruebas sobre los componentes que acabamos de crear.

## Probado el entorno:

Nuxtjs viene integrado y preconfigurado con Jest con una libreria llamada [jest](https://jestjs.io/), además vuejs nos provee de una libreria llamada `@vue/test-utils`, con la que podremos montar nuestros componentes desde la consola, sin tener que abrir un navegador para testearlo.

Abre la consola y prueba el siguiente comando:

```shell
npm test
```

Si todo ha ido correctamente, veras que la consola empieza a ejecutar una serie de checks y de procesos testeando el componente `Logo.vue`.


El fichero que se ejecuta para comprobar el funcionamiento del componente `Logo.vue` lo puedes encontrar en la carpeta `test/Logo.spec.js`. Por defecto, para que la herramienta de Jest entienda que ese fichero es un fichero para pasar un test, tiene que tener siempre la extensión `*.spec.js`, y podemos guardarlo en cualquier parte de nuestro proyecto. 

## Entendiendo `Logo.spec.js`

```js
import { mount } from '@vue/test-utils'
import Logo from '@/components/Logo.vue'

describe('Logo', () => {
  test('is a Vue instance', () => {
    const wrapper = mount(Logo)
    expect(wrapper.isVueInstance()).toBeTruthy()
  })
})
```

El código anterior tiene una estructura muy sencilla.

- `import { mount } from '@vue/test-utils'`

Primero, importamos de la libreria `@vue/test-utils` el método mount que nos permite montar el componente, simulando que lo hacemos desde un navegador.

- `import Logo from '@/components/Logo.vue'`

Importamos el componente que queremos probar y testear.

- `describe('Logo', () => {})`

El método **descripe** inicializa un scope o entonrno de ejecución de pruebas, es el sitio donde definiremos algunas variables, haremos algunos calculos o inicializaremos funciones que simulen algun comportamiento especifico (Una peticion HTTP por ejemplo.)

La función recive por parametro una descripción del contexto que queremos probar y del cual queremos hacerle los test y despues una función que ejecutara los test en orden. Es una buena práctica, poner el nombre del componente o alguna funcionalidad concreta.

- `test('is a Vue instance', () => {})`

La función **test** es la que realmente en ultima instancia lanzara el test, de igual manera, el primer parametro es una descripción del test (la prueba que se va a realiar) y despues la función que ejecutara el test.

En nuestro ejemplo del componente `Logo.vue`, el text *monta* el componente inicializandolo en un wrapper, el cual comprueba que realamnere se ha montado correctamente mediante la comprobación `expect(wrapper.isVueInstance()).toBeTruthy()`

Existen multitud de **expects** y comprobaciones.

[Lista de expects](https://jestjs.io/docs/en/expect)

### ⚒️ RECOMENDACIÓN:


### 📚 Referencias y ayudas
- [Jest](https://jestjs.io/)
- [Guía Oficial de instalación Nuxtjs](https://nuxtjs.org/guide/installation)
- [Git](https://www.git-scm.com/)
- [GitHub](https://github.com/)