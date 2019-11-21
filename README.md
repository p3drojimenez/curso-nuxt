# 📗 Clase 3:

 Diferencias entre **SPA** y **SSR**.

 Con nuxtjs podemos generar estos dos tipos de páginas, pero primero de todo debemos saber que es cada una y conocer así sus diferencias.

 Las SPA, son páginas que se renderizan de una sola vez, exactamente no es así, pero sí que necesita que toda o casi toda la parte lógica de la aplicación este de cara al cliente. Su rendimiento dependerá de como e grande sean esos ficheros y la velocidad de descarga. Es bueno por ejemplo para equipos con unos procesadores decentes y nuevos.

 Una SPA, no tiene páginas como tal si no vistas y todas son accesibles desde el root, es decir, que si por ejemplo quisiéramos ir al detalle de un restaurante, que la url seria tipo "restaurante/nombre-del-restaurante", no podríamos hacerlo y deberíamos ir al a home e ir pinchando en los enlaces correspondientes hasta llegar allí. Tiene sus ventajas y sus inconvenientes.

 Los robots de indexación, tipo google, tienen problemas para indexar este tipo de páginas ya que esas rutas que hemos dicho antes, no son accesibles desde una url normal.


 Y las páginas SPA se ejecutan siempre del lado del cliente.

 Por otro lado, tenemos las SSR o también llamadas isomorfas. Estas páginas son accesibles desde el exterior, ya que hay un prerenderizado de las páginas por parte del servidor, es decir, que en el momento de generar nuestra aplicación y subirla al servidor, se han de generar cada una de esas páginas. El proceso es muy rápido y aun que tengamos un e-comerce con cientos de páginas no se demora mucho.


Son muy buenas para indexar en los buscadores, tiene sentido, ya que google las conoce o mejor dicho, puede acceder a ellas.


Y parte de su renderizado es por parte del servidor, esto facilita dos cosas, lo primero que las páginas se han renderizado en el servidor y por lo tanto se puede cachear a otros usuario, haciendo mucho más rápido su acceso y dos elimina carga de procesado del lado del cliente, por lo que si nuestra app es muy grande, el usuario solo vera las partes que el requiera, que haya solicitado y no todas las páginas.

