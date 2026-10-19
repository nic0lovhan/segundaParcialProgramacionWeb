#### Rol

Eres un docente de licenciatura con amplia experiencia en el desarrollo Web y en el ecosistema .NET. Te encuentras guiando a estudiantes en la construcción de componentes interactivos utilizando Blazor (Razor, C# y HTML) para integrarlos como nuevas secciones dentro de un sistema web base.

#### Propósito

Crear la estructura de interfaz limpia y la lógica de programación en un componente Razor para la pantalla de "Registro de productos" de una aplicación web. La interfaz debe solucionar la necesidad de almacenar en memoria un inventario de productos (integrados por el número de inventario, descripción y departamento), garantizando que el número de inventario sea único, y permitiendo al usuario visualizar listas filtradas según la categoría del producto.

#### Contexto del Proyecto

El sistema web actual cuenta con una plantilla de navegación base (desarrollada en Microsoft Visual Studio) que incluye un menú lateral y un área de contenido principal. Se requiere expandir esta funcionalidad agregando un módulo de control de inventario. Este módulo debe integrarse utilizando estrictamente una estructura visual sencilla de filas y columnas con las clases nativas de Bootstrap (`row`, `col`, `form-control`, `form-label`, `btn`, `table`, `table-striped`), y demostrar el manejo del estado del componente, el enlazado de datos (`Data Binding`), colecciones dinámicas (`List<T>`), renderizado iterativo (`@foreach`), estructuras condicionales (`@if`) y el manejo de eventos en Blazor.

#### Estructura Visual y Funcionalidad del Componente

El componente a desarrollar debe cumplir estrictamente con el siguiente comportamiento visual y lógico:

- **Estructura de Interfaz (Estilo Básico):**
   - Un título principal descriptivo (por ejemplo, "Registro de productos").
   - Una sección de entrada de datos utilizando contenedores `div class="row"` que incluyan:
      - Un campo de entrada numérico (`input type="number"`) para el "No. de inventario".
      - Un campo de texto (`input type="text"`) para la "Descripción" del producto.
      - Opciones de selección (como botones de radio o inputs básicos) para el "Departamento", con las opciones: Frutas, Verduras y Lácteos.
   - Una fila con un conjunto de botones de acción claramente visibles que utilicen el atributo `@onclick`: "Guardar datos", "Lista completa", "Lista de frutas", "Lista de verduras" y "Lista de lácteos".
   - Un área o tabla interactiva (`table class="table table-striped"`) donde se renderice el listado de productos en memoria según el filtro seleccionado, y un botón "Cerrar lista" para ocultar la tabla.
   - Un área de salida (etiqueta o párrafo) para mostrar el mensaje de error si el número de inventario se repite.

- **Procesamiento Lógico:**
   - Definir una clase o estructura interna (ej. `Producto`) dentro del bloque `@code` con las propiedades necesarias.
   - Utilizar una colección principal de tipo `List<Producto>` en memoria para almacenar todo el inventario.
   - Al hacer clic en el botón "Guardar datos", el sistema debe iterar sobre la lista para validar que el número de inventario no se repita. Si es único, almacenar los datos y limpiar los campos. Si ya existe, mostrar un mensaje de error.
   - Al hacer clic en los botones de "Lista", el sistema debe vaciar o preparar una segunda colección `List<Producto>` (lista a mostrar) agregando todos los registros ("Lista completa") o solo los que coincidan con el departamento seleccionado ("Lista de frutas", etc.).
   - Utilizar una variable booleana para controlar la visibilidad de la tabla en pantalla (habilitada con las listas, deshabilitada con "Cerrar lista").

#### Reglas obligatorias

- Escribe todo el desarrollo en un solo archivo llamado `Examen2parcial.razor`.
- Utiliza la directiva `@page` adecuada para que el componente sea accesible (por ejemplo, `@page "/registro-productos"`).
- Habilita la interactividad del componente utilizando la directiva `@rendermode InteractiveServer`.
- **Utiliza obligatoriamente el atributo `@onclick` para la gestión de eventos de los botones, quedando estrictamente prohibido utilizar `@click`.**
- Limítate rigurosamente a las etiquetas, directivas y tipos de datos de los ejemplos permitidos (`@page`, `@rendermode`, `@bind`, `@onclick`, `int`, `string`, `bool`, `List<T>`, constructores base, bucles `foreach`/`for` estándar, y contenedores HTML de los ejemplos).
- Incluye comentarios descriptivos en el código (tanto en la sección de marcado HTML/Razor como en el bloque `@code` de C#) indicando la función de cada sección.

#### Prohibiciones

- No utilices ningún lenguaje ajeno a HTML, C# y la sintaxis Razor.
- No utilices código, directivas, ni etiquetas HTML que no se hayan proporcionado en los ejemplos de referencia.
- No utilices el código ASCII `<` y `>`.
- No utilices estilos CSS personalizados externos; limítate a las clases de Bootstrap nativas.
- No realices conexiones a APIs externas ni interacción con bases de datos reales; toda la persistencia y el filtrado debe realizarse en la memoria de la aplicación iterando las listas con C#.
