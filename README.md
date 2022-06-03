# Trabajo práctico #2
### **-- By Sid & Co. --**

**Link al uml:** _https://app.diagrams.net/#G1eYk6r_WHObf-nPjhqyYE-D9SZVmpDg_4_

# Explicacion del codigo - Paso a paso

### Aclaraciones para todos los métodos:
* **override**: En una declaración o definición de un método de clase, el especificador `override` garantiza que la función anule una función virtual de una clase madre.
###
* **const**: En una declaración o definición de un método de clase, el especificador `const` se usa cuando se sabe que el atributo que va a devolver no va a cambiar nunca desde el momento que se lo inicializa hasta el fin del programa.
###
* **getline()**: Se utiliza para leer el flujo de entrada en situaciones en las que es posible que el dato que ingrese el usuario pueda llegar a contener espacios, y esta función nos permite leer hasta que encuentra un salto de línea y así poder tener almacenado el dato entero.


## Main:
Cuando el programa comienza a correr entra en el archivo "main.cpp" y el primer método que corre es `int main`. En este método instanciamos 7 objetos esenciales para el correcto funcionamiento del código. Los mismos son:

* `ArchivoEscritores`
* `Lista` de tipo `Escritor*`
* `Lista* `de tipo `Escritor*`
* `ArchivoLecturas`
* `Lista` de tipo `Lectura*`
* `Lista*` de tipo `Lectura*`
* Menu!!!

## ProcesarArchivos:
Esta clase es madre de las clases ArchivoEscritores y ArchivoLecturas. Algunos de sus métodos no son usados por sí misma si no que son heredados por sus hijas, pero tiene métodos propios.

### Atributos:

* ifstream: `archivo`
###### (este tipo de dato `ifstream` es proporcionado por la librería `<fstream>` que es la que nos permite realizar la lectura de archivos)

* string: `texto`

* int: `indice`

### Métodos

* Constructor `ProcesarArchivos`: Se ocupa de inicializar los atributos del objeto `texto` e `índice` en texto vacío o -1 respectivamente.
### 
* `virtual void procesarDatos {}`: Este método es heredado por las hijas.
###
* `virtual void aperturaArchivo {}`: Este método es heredado por las hijas.
###
* `bool indiceReiniciado const`: Se ocupa de indicar si el índice es igual o no a 1. Si el índice es igual a 1, entonces el índice está reiniciado.
###
* `void cerrarArchivo`: Se ocupa de cerrar el archivo.
###
* `bool archivoFinalizado`: Se ocupa de indicar si el archivo sigue teniendo líneas por leer.
###
* `void leerLinea`: Se ocupa de obtener una línea de texto del archivo.
###
* `void establecerTexto`: Se ocupa de establecer el valor de texto a el string recibido por argumento.



## ArchivoEscritores:
Esta clase es la clase que nos permite procesar todos los datos que se encuentren en el archivo de los escritores.

### Atributos:

* string: `nombreApellido`, `nacionalidad`

* int: `anioNacimiento`, `anioFallecimiento`

### Métodos:

* Constructor `ArchivoEscritores`: Se ocupa de inicializar todos los atributos del objeto en -1 o texto vacío.
###
* `void aperturaArchivo override`: Se ocupa de abrir el archivo que contiene los datos de los escritores. En el caso de no poder hacerlo muestra un mensaje de error y cierra el programa.
###
* `void procesarDatos override`: Se ocupa de leer una línea y guardar ese dato en el atributo correspondiente.
### 
* `void comprobarFaltaDatos`: Se ocupa de verificar la falta de datos en los años de fallecimiento y nacimiento y los guarda con -1.
### 
* `Escritor* crearEscritor`: Se ocupa de instancia un objeto `Escritor` a través de un `new` pasándo los atributos antes guardados en `procesarDatos`. Por último devuelve el puntero que apunta a ese objeto.
###
* `Lista<Escritor*> porcesarArchivoEscritores`: Se ocupa de crear una `Lista` y llamar a la instanciación de los escritores individualmente para darlos de alta, así obtenemos y devolvemos una `Lista` de tipo `Escritor*`.
###
* `void establecerAnioFallecimiento`: Se ocupa de establecer un valor al atributo `anioFallecimiento` cuando se quiere modificar desde afuera de los métodos de `ArchivoEscritores`.
###
* `void establecerNombreApellido`: Se ocupa de establecer un valor al atributo `nombreApellido` cuando se quiere modificar desde afuera de los métodos de `ArchivoEscritores`.
###
* `void establecerNacionalidad`: Se ocupa de establecer un valor a el atributo `nacionalidad` cuando se quiere modificar desde afuera de los métodos de `ArchivoEscritores`.
###
* `void establecerAnioNacimiento`: Se ocupa de establecer un valor a el atributo `anioNacimiento` cuando se quiere modificar desde afuera de los métodos de `ArchivoEscritores`.
###
* `string obtenerNombreApellido`: Este método consulta el atributo `nombreApellido` del escritor y lo devuelve en forma de string.


## ArchivoLecturas:
### Atributos:

* Lista<Escritor*>*: `listaEscritores`

* string: `tipoLectura`, `titulo`, `subtema`, `auxiliarReferencia`

* char*: `descripcion`

* Escritor*: `autor`

* int: `minutosLectura`, `anio`, `referencia`, `genero`

### Métodos:

* Constructor `ArchivoLecturas ()`: Se ocupa de inicializar todos los atributos del objeto en -1, texto vacio o null.
###
* Constructor `ArchivoLecturas = default`: Este método es un constructor por default para poder usar a ArchivoLecturas como Dato en los templates.
###
* `void aperturaArchivo override`: Se ocupa de abrir el archivo donde se encuentran los datos de las lecturas. En el caso de no poder hacerlo muestra un mensaje de error y cierra el programa.
###
* `void procesarDatos`: Se ocupa de procesar todos los datos y guardarlos en sus respectivos atributos del objeto `ArchivoLectura`.
###
* `void convertirGenero`: Se ocupa de transformar el número representativo del enum de géneros en un string.
###
* `Poema* crearPoema`: Se ocupa de instancia un objeto `Poema` a través de un `new` pasandole los atributos antes guardados en `procesarDatos`. Por ultimo devuelve el puntero que apunta a ese objeto.
###
* `Cuento* crearCuento`: Se ocupa de instancia un objeto `Cuento` a través de un `new` pasándole los atributos antes guardados en `procesarDatos`. Por último devuelve el puntero que apunta a ese objeto.
###
* `Novela* crearNovela`: Se ocupa de instancia un objeto `Novela` a través de un `new` pasándo los atributos antes guardados en `procesarDatos`. Por último devuelve el puntero que apunta a ese objeto.
###
* `NovelaHistorica* crearNovelaHistorica`: Se ocupa de instancia un objeto `NovelaHistorica` a traves de un `new` pasandole los atributos antes guardados en `procesarDatos`. Por ultimo devuelve el puntero que apunta a ese objeto.
###
* `Lectura* crearLecura`: Se ocupa de instanciar un objeto `Lectura` y segun su tipo llama al método correspondiente para crear la lectura.
###
* `void convertirReferencia`: Se ocupa de convertir el número de referencia del autor a un entero.
###
* `void asignarAutor`: Se encarga de asignar un autor de la lista de escritores al atributo `autor` según el número de referencia de la lectura.
###
* `Lista<Lectura*> procesarArchivoLecturas`: Se encarga de instanciar un objeto `Lista` de tipo `Lectura*` según los datos del archivo.
###
* `void establecerReferencia`: Se ocupa de establecer un valor a el atributo `referencia` cuando se quiere modificar desde afuera de los métodos de `ArchivoLecturas`.
###
* `void establecerTipoLectura`: Se ocupa de establecer un valor al atributo `tipoLectura` cuando se quiere modificar desde afuera de los métodos de `ArchivoLecturas`.
###
* `void establecerTitulo`: Se ocupa de establecer un valor a el atributo `título` cuando se quiere modificar desde afuera de los métodos de `ArchivoLecturas`.
###
* `void establecerSubtema`: Se ocupa de establecer un valor a el atributo `subtema` cuando se quiere modificar desde afuera de los métodos de `ArchivoLecturas`.
###
* `void establecerDescripcion`: Se ocupa de establecer un valor al atributo `descripcion` cuando se quiere modificar desde afuera de los métodos de `ArchivoLecturas`.
###
* `void establecerAutor`: Se ocupa de establecer un valor a el atributo `autor` cuando se quiere modificar desde afuera de los métodos de `ArchivoLecturas`.
###
* `void establecerMinutosLectura`: Se ocupa de establecer un valor al atributo `minutosLectura` cuando se quiere modificar desde afuera de los metodos de `ArchivoLecturas`.
###
* `void establecerAnio`: Se ocupa de establecer un valor a el atributo `anio` cuando se quiere modificar desde afuera de los métodos de `ArchivoLecturas`.
###
* `string obtenerTipoLectura`: Este método consulta el atributo `tipoLectura` de la lectura y lo devuelve en forma de string.

## Menu:
### Atributos:

* int: `opcion`

* string: `datoUsuario`

* bool `operacionExitosa`, `datoEncontrado`

* Escritor* `escritorActual`

* Lectura* `lecturaActual`

* Lista<Lectura*>* `listaLecturas`
* Lista<Escritor*>* `listaEscritores`

* ArchivoLecturas `lectura`
* ArchivoEscritores `escritor`

### Métodos:

* Constructor `Menu`: Se ocupa de inicializar los atributos del objeto en texto vacío, -1, false o null.
###
* `void mostrarMenu`: Se ocupa de mostrar todas las opciones disponibles para usar el programa, recibe la opción elegida.
###
* `void mensajeExito`: Se ocupa de mostrar por consola un mensaje de éxito.
###
* `void mensajeError`: Se ocupa de mostrar por consola un mensaje de error.
###
* `void verificarOperacion`: Se ocupa de verificar que la operación del programa se haya llevado a cabo.
###
* `opcionUsuario`: Se ocupa de tomar la opción elegida por el usuario y llama al método necesario para ejecutar esa opción.
###
* `int obtenerOpcion`: Se ocupa de hacer una consulta a la opción elegida por el usuario y la devuelve.

#### - Sección menú lecturas -
* `void pedirDescripcion`: Se ocupa de pedir una descripción para la novela histórica.
###
* `void pedirSubtema`: Se ocupa de pedir al usuario un subtema y dependiendo el tipo de lectura que se está instanciando se pide un atributo diferente.
###
* `void pedirGenero`: Se ocupa de pedirle al usuario el género de la novela.
###
* `void pedirTipoLectura`: Se ocupa de pedir al usuario el tipo de lectura que quiere crear.
###
* `void pedirDatosLEctura`: Se ocupa de pedir todos los datos necesarios para crear la lectura y completar su atributos.
###
* `void verificarEscritorAnonimo`: Se ocupa de preguntar al usuario si el autor de la lectura es anónimo.
###
* `void agregarLectura`: Se ocupa de llamar a los métodos que piden los datos de la lectura y a la que da de alta a la lista de lecturas.
###
* `void quitarLectura`:  Se ocupa de pedir los datos necesarios para llamar al método que da de baja las lecturas en la lista.
###
* `void sortearLectura`: Se ocupa de elegir una lectura aleatoriamente.
###
* `void listarLecturas`: Se ocupa de listar las lecturas en el orden que están guardadas.
###
* `void listarLecturasAnios`: Se ocupa de pedir al usuario los años para listar las lecturas desde y hasta los años indicados.
###
* `void listarLecturasEscritor`: Se ocupa de pedir al usuario el nombre de un autor y listar las lecturas escritas por el autor ingresado.
###
* `void mostrarGeneros`: Se ocupa de todas las opciones de géneros para novela.
###
* `void listarNovelasGenero`: Se ocupa de pedir al usuario un género de novela y listar las novelas que pertenecen al género ingresado.

#### - Seccion menu escritores -
* `void buscarEscritor`: Se ocupa de  buscar un escritor.
###
* `void pedirDatosEscritor`: Se ocupa de pedir al usuario que ingrese los datos de un escritor y de verificar que el escritor que se intenta agregar no exista en la lista de escritores.
###
* `bool tieneAnioFallecimiento`: Se ocupa de verificar si el escritor el cual se está consultando tiene o no anio de fallecimiento.
###
* `void confirmarCambioFallecimiento`: Se ocupa de pedirle al usuario que confirme si quiere cambiar el año de fallecimiento a pesar de que ya tenga uno existente.
###
* `void modificarAnio`: Se ocupa de pedir al usuario que ingrese el año de fallecimiento nuevo que quiere agregar.
###
* `void modificarEscritor`: Se ocupa de pedir al usuario que ingrese el nombre y apellido del autor que quiere modificar.
###
* `void listarEscritores`: Se ocupa de listar todos los escritores de la lista.

#### - Sección armar Cola -
* `void armarCola`: Se ocupa de instanciar una `Cola` y una `Lista` auxiliar. También llama a los respectivos métodos para dar de alta lecturas en la lista auxiliar, preguntar si la lectura fue leída. Por último copia la lista a la cola instanciada.
###
* `void menuLecturaLeida`: Se ocupa de preguntar al usuario si una lectura fue leída o no.
###
* `void menuCola`: Se ocupa de mostrar la cola y llama a los respectivos métodos para dar las opciones al usuario.
###
* `void opcionesCola`: Se ocupa de mostrar al usuario  las opciones para la cola.
###
* `void salir`: se ocupa de dar un mensaje de despedida.

## Lista:
### Atributos:

* Nodo<Dato>* `primero`, `cursor`

* int `cantidad`

### Métodos:

* Constructor `Lista`: Se ocupa de inicializar los atributos de `Lista` en null o 0.
###
* Destructor `~Lista`: Se ocupa de liberar la memoria reservada durante la ejecución del programa para las listas.
###
* `void baja`: Se ocupa de dar de baja nodos y de apuntar los punteros con el fin de no perder los datos de la lista.
###
* `void alta`: Se ocupa de dar de alta los datos nuevos que se ingresan a la lista.
###
* `int actualizarDatoCursorAlta`: Se ocupa de pedir los datos del `cursor` según necesite el método que la llama.
###
* `void altaOrdenada`: Se ocupa de hacer llamadas a los metodos que dan de alta a la lista de forma ordenada según el año de publicación.
###
* `void altaComparacionInicialIgual`: Modularización de `altaOrdenada`. Se ocupa de efectuar el alta del nuevo dato ingresado.
###
* `void altaComapracionInicialMayor`: Modularización de `altaOrdenada`. Se ocupa de efectuar el alta del nuevo dato ingresado. También hace llamada al método que da de alta en el ultimo lugar de la lista si es que es necesario.
###
* `void altaComparacionInicialMenor`: Modularización de `altaOrdenada`. Se ocupa de efectuar el alta del nuevo dato ingresado. Tambien hace llamada al método que da de alta en el primer lugar de la lista si es que es necesario.
###
* `void altaPrimerELemento`: Se ocupa de dar de alta el nuevo dato en el primer lugar de la lista.
###
* `void altaUltimoElemento`: Se ocupa de dar de alta el nuevo dato en el último lugar de la lista.
###
* `int comparar`: Compara si el nuevo dato es menor o mayor al del `cursor` para realizar el alta.
###
* `void listarIntervalo`: Se ocupa de marcar desde que nodo hasta que nodo tiene cumplen los requisitos para ser mostrados por intervalo de anio.
###
* `bool elementoEncontrado`: Se ocupa de encontrar coincidencias entre año de publicación y título ingresado por el usuario y los de alguna de las lecturas existentes.
###
* `void bajaComparacionInicialIgualMenor`: Se ocupa de dar de baja una lectura según su año de publicación y título.
###
* `void bajaComparacionInicialMayor`: Se ocupa de dar de baja una lectura según su año de publicación y título.
###
* `void bajaOrdenada`: Se ocupa de hacer llamadas a los métodos que se encargan de dar de baja elementos de una lista según año de publicación y título.
###
* `void mostrarElementos`: Se ocupa de mostrar los elementos de una lista.
###
* `Dato consulta`: Se ocupa de obtener un nodo y devuelve sus datos.
###
* `bool vacia`: Se ocupa de preguntar si la lista está vacía.
###
* `int obtenerCantidad`: Se ocupa de obtener la cantidad de elementos que hay dentro de la lista empezando a contar desde 1.
###
* `void apuntarCursor`: Se ocupa de apuntar el `cursor` a un nodo de la lista válida.
###
* `Dato iterarLista`: Se ocupa de iterar la lista para devolver un nodo específico.
###
* `Dato datoPrimero`: Se ocupa de obtener el dato dentro del atributo puntero `primero`.
###
* `void reiniciarCursor`: Se ocupa de apuntar al `cursor` al primero.
###
* `Nodo<Dato>* obtenerNodo`: Se ocupa de obtener un nodo según su posición en la lista.

## Nodo:
### Atributos:

* Dato `dato`

* Nodo<Dato>* `siguiente`

### Métodos:

* Constructor `Nodo`: Se ocupa de inicializar los atributos en null o con el tipo de dato pasado.
###
* `void cambiarSiguiente`: Se ocupa de apuntar el siguiente nodo recibido.
###
* `Dato obtenerDato`: Se ocupa de hacer una consulta al atributo dato de un nodo y lo devuelve.
###
* `Nodo<Dato>* obtenerSiguiente`: Se ocupa de obtener a quién apunta el puntero `siguiente` del nodo actual.

## Escritor:
### Atributos:

* string `nombreApellido`, `nacionalidad`

* int `anioNacimiento`, `aniofallecimiento`

### Métodos:

* Constructor `Escritor`: Se ocupa de inicializar los atributos con los respectivos datos del autor.
###
* Constructor `Escritor = default`: Este método es un constructor por default para poder usar a Escritor como Dato en los templates.
###
* `void mostrar`: Se ocupa de mostrar los datos de los autores.
###
* `void modificarFallecimiento`: Se ocupa de establecer un valor al atributo `anioFallecimiento` cuando se quiere modificar desde afuera de los métodos de `Escritor`.
###
* `string obtenerNombreApellido`: Este método consulta el atributo `nombreApellido` del escritor y lo devuelve en forma de string.
###
* `string obtenerNacionalidad`: Este método consulta el atributo `nacionalidad` del escritor y lo devuelve en forma de string.
###
* `int obtenerAnioNacimiento`: Este método consulta el atributo `anioNacimiento` del escritor y lo devuelve en forma de int.
###
* `int obtenerAnioFallecimiento`: Este método consulta el atributo `anioFallecimiento` del escritor y lo devuelve en forma de int.

## Lectura:
### Atributos:

* string `titulo`

* int `minutos`, `anioPublicacion`

* Escritor* `autor`

### Métodos:

* Constructor `Lectura`: Se ocupa de inicializar los atributos con los respectivos datos de la lectura.
###
* Constructor `Lectura = default`: Este metodo es un constructor por default para poder usar a Lectura como Dato en los templates.
###
* Destructor `~Lectura = default`: Este método es un destructor por default ya que es necesario que primero se destruyan las hijas y luego la clase madre.
###
* `virtual void mostrar {}`: Este método es heredado por las hijas.
###
* `void mostrarAutor`: Se ocupa de mostrar los datos del autor de la lectura.
###
* `string obtenerTitulo const`: Este método consulta el atributo `titulo` de la lectura y lo devuelve en forma de string.
###
* `int obtenerMinutos const`: Este método consulta el atributo `minutos` de la lectura y lo devuelve en forma de int.
###
* `int obtenerAnioPublicacion const`: Este método consulta el atributo `anioPublicacion` de la lectura y lo devuelve en forma de int.
###
* `Escritor* obtenerAutor`: Este método consulta el atributo `autor` de la lectura y lo devuelve en forma de Escritor*.

## Cuento:
### Atributos:

* string `libro`

### Métodos:

* Constructor `Cuento`: Se ocupa de inicializar los atributos con los respectivos datos de Cuento.
###
* Destructor `~Cuento override = default`: Este método es un destructor por default ya que es necesario que primero se destruyan las hijas y luego la clase madre.
###
* `void mostrar override`: Se ocupa de mostrar los datos del Cuento.
###
* `string obtenerLibro`: Este método consulta el atributo `libro` del cuento y lo devuelve en forma de string.

## Novela:
### Atributos:

* int `genero`

### Métodos:

* Constructor `Novela`: Se ocupa de inicializar los atributos con los respectivos datos de Novela.
###
* Destructor `~Novela override = default`: Este método es un destructor por default ya que es necesario que primero se destruyan las hijas y luego la clase madre.
###
* `void mostrar override`: Se ocupa de mostrar los datos de la Novela.
###
* `void mostrarGenero const`: Se ocupa de mostrar el género de la Novela.
###
* `int obtenerGenero const`: Este método consulta el atributo `genero` de la novela y lo devuelve en forma de int.

## NovelaHistorica:
### Atributos:

* char* `tema`

### Métodos:

* Constructor `NovelaHistorica`: Se ocupa de inicializar los atributos con los respectivos datos de NovelaHistorica.
###
* Destructor `~NovelaHistorica override = default`: Este método es un destructor por default ya que es necesario que primero se destruyan las hijas y luego la clase madre.
###
* `void mostrar override`: Se ocupa de mostrar los datos de la NovelaHistorica.
###
* `char* obtenerTema`: Este método consulta el atributo `tema` de la NovelaHistorica y lo devuelve en forma de char*.

## Poema:
### Atributos:

* int `versos`

### Métodos:

* Constructor `Poema`: Se ocupa de inicializar los atributos con los respectivos datos de Poema.
###
* Destructor `~Poema override = default`: Este método es un destructor por default ya que es necesario que primero se destruyan las hijas y luego la clase madre.
###
* `void mostrar override`: Se ocupa de mostrar los datos del Poema.
###
* `int obtenerVersos`: Este método consulta el atributo `versos` del Poema y lo devuelve en forma de int.

## Cola:
### Atributos:

* Nodo<Dato>* `primero`
* Nodo<Dato>* `ultimo`

### Métodos:

* Constructor `Cola`: Se ocupa de inicializar los atributos con los respectivos datos de Cola.
###
* Destructor `~Cola`: Se ocupa de liberar la memoria dinámica de sus elementos.
###
* `void alta`: Se ocupa de dar de alta los datos nuevos que se ingresan a la cola.
###
* `void baja`: Se ocupa de eliminar el primer Nodo de la cola, apunta el puntero primero al siguiente y si no hay más Nodos en la cola, resetea primero a nullptr.
###
* `Dato consulta`: Se ocupa de obtener el Dato del primer elemento y lo devuelve en forma de Dato.
###
* `bool vacia`: Se ocupa de preguntar si la cola está vacía.
