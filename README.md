# Trabajo practico #2 
### **-- By Sid & Co. --**

**Link al uml:** _https://app.diagrams.net/#G1eYk6r_WHObf-nPjhqyYE-D9SZVmpDg_4_ 

# Explicacion del codigo - Paso a paso

### Aclaraciones para todos los metodos:
* **override**: En una declaración o definición de un metodo de clase, el especificador `override` garantiza que la función anule una función virtual de una clase madre.
###
* **const**: En una declaración o definición de un metodo de clase, el especificador `const` se usa cuando se sabe que el atributo que va a devolver no va a cambiar nunca desde el momento que se lo inicializa hasta el fin del programa.
###
* **getline()**: Se utiliza para leer el flujo de entrada en situaciones en las que es posible que el dato que ingrese el usuario pueda llegar a contener espacios, y esta funcion nos permite leer hasta que encuentra un salto de linea y asi poder tener almacenado el dato entero.


## Main:
Cuando el programa comienza a correr entra en el archivo "main.cpp" y el primer metodo que corre es `int main`. En este metodo instanciamos 7 objetos esenciales para el correcto funcionamiento del codigo. Los mismos son:

* `ArchivoEscritores`
* `Lista` de tipo `Escritor*`
* `Lista* `de tipo `Escritor*`
* `ArchivoLecturas`
* `Lista` de tipo `Lectura*`
* `Lista*` de tipo `Lectura*`
* Menu!!!

## ProcesarArchivos:
Esta clase es madre de las clases ArchivoEscritores y ArchivoLecturas. Algunos de sus metodos no son usados por si misma si no que son heredados por sus hijas, pero tiene metodos propios.

### Atributos:

* ifstream: `archivo`
###### (este tipo de dato `ifstream` es proporcionado por la libreria `<fstream>` que es la que nos permite realizar la lectura de archivos)

* string: `texto`

* int: `indice`

### Metodos

* Constructor `ProcesarARchivos`: Se ocupa de inicializar los atributos del objeto `texto` e `indice` en texto vacio o -1 respectivamente.
### 
* `virtual void procesarDatos {}`: Este metodo es heredado por las hijas.
###
* `virtual void aperturaArchivo {}`: Este metodo es heredado por las hijas.
###
* `bool indiceReiniciado const`: Se ocupa de indicar si el indice es igual o no a 1. Si indice es igual a 1, entonces el indice esta reinciado. 
###
* `void cerrarArchivo`: Se ocupa de cerrar el archivo.
###
* `bool archivoFinalizado`: Se ocupa de indicar si el archivo sigue teniendo lineas por leer.
###
* `void leerLinea`: Se ocupa de obtener una linea de texto del archivo.
###
* `void establecerTexto`: Se ocupa de establecer el valor de texto a el string recibido por argumento.



## ArchivoEscritores:
Esta clase es la clase que nos permite procesar todos los datos que se encuentren en el archivo de los escritores.

### Atributos:

* string: `nombreApellido`, `nacionalidad`

* int: `anioNacimiento`, `anioFallecimiento`

### Metodos:

* Constructor `ArchivoEscritores`: Se ocupa de inicializar todos los atributos del objeto en -1 o texto vacio.
###
* `void aperturaArchivo override`: Se ocupa de abrir el archivo que contiene los datos de los escritores. En el caso de no poder hacerlo muestra un mensaje de error y cierra el programa.
###
* `void procesarDatos override`: Se ocupa de leer una linea y guardar ese dato en el atributo correspondiente.
### 
* `void comprobarFaltaDatos`: Se ocupa de verificar la falta de datos en los años de fallecimiento y nacimiento y los guarda con -1.
### 
* `Escritor* crearEscritor`: Se ocupa de instancia un objeto `Escritor` a traves de un `new` pasandole los atributos antes guardados en `procesarDatos`. Por ultimo devuelve el puntero que apunta a ese objeto.
###
* `Lista<Escritor*> porcesarArchivoEscritores`: Se ocupa de crear una `Lista` y llamar a la instanciacion de los escritores individualmente para darlos de alta, asi obtenemos y devolvemos una `Lista` de tipo `Escritor*`.
###
* `void establecerAnioFallecimiento`: Se ocupa de establecer un valor a el atributo `anioFallecimiento` cuando se quiere modificar desde afuera de los metodos de `ArchivoEscritores`.
###
* `void establecerNombreApellido`: Se ocupa de establecer un valor a el atributo `nombreApellido` cuando se quiere modificar desde afuera de los metodos de `ArchivoEscritores`.
###
* `void establecerNacionalidad`: Se ocupa de establecer un valor a el atributo `nacionalidad` cuando se quiere modificar desde afuera de los metodos de `ArchivoEscritores`.
###
* `void establecerAnioNacimiento`: Se ocupa de establecer un valor a el atributo `anioNacimiento` cuando se quiere modificar desde afuera de los metodos de `ArchivoEscritores`.
###
* `string obtenerNombreApellido`: Este metodo consulta el atributo `nombreApellido` del escritor y lo devuelve en forma de string.


## ArchivoLecturas:
### Atributos:

* Lista<Escritor*>*: `listaEscritores`

* string: `tipoLectura`, `titulo`, `subtema`, `stringReferencia`

* char*: `descripcion`

* Escritor*: `autor`

* int: `minutosLectura`, `anio`, `referencia`, `genero`

### Metodos:

* Constructor `ArchivoLecturas ()`: Se ocupa de inicializar todos los atributos del objeto en -1, texto vacio o null.
###
* Constructor `ArchivoLecturas = default`: Este metodo es un costructor por default para poder usar a ArchivoLecturas como Dato en los templates.
###
* `void aperturaArchivo override`: Se ocupa de abrir el archivo donde se encuentran los datos de las lecturas. En el caso de no poder hacerlo muestra un mensaje de error y cierra el programa.
###
* `void procesarDatos`: Se ocupa de procesar todos los datos y guardarlos en sus respectivos atributos del objeto `ArchivoLectura`.
###
* `void convertirGenero`: Se ocupa de transformar el numero representativo del enum de generos en un string.
###
* `Poema* crearPoema`: Se ocupa de instancia un objeto `Poema` a traves de un `new` pasandole los atributos antes guardados en `procesarDatos`. Por ultimo devuelve el puntero que apunta a ese objeto.
###
* `Cuento* crearCuento`: Se ocupa de instancia un objeto `Cuento` a traves de un `new` pasandole los atributos antes guardados en `procesarDatos`. Por ultimo devuelve el puntero que apunta a ese objeto.
###
* `Novela* crearNovela`: Se ocupa de instancia un objeto `Novela` a traves de un `new` pasandole los atributos antes guardados en `procesarDatos`. Por ultimo devuelve el puntero que apunta a ese objeto.
###
* `NovelaHistorica* crearNovelaHistorica`: Se ocupa de instancia un objeto `NovelaHistorica` a traves de un `new` pasandole los atributos antes guardados en `procesarDatos`. Por ultimo devuelve el puntero que apunta a ese objeto.
###
* `Lectura* crearLecura`: Se ocupa de instanciar un objeto `Lectura` y segun su tipo llama al metodo correspondiente para crear la lectura.
###
* `void convertirReferencia`: Se ocupa de converir el numero de referencia del autor a un entero.
###
* `void asignarAutor`: Se encarga de asignar un autor de la lista de escritores al atributo `autor` segun el numero de referencia de la lectura.
###
* `Lista<Lectura*> procesarArchivoLecturas`: Se encarga de instancia un objeto `Lista` de tipo `Lectura*` segun los datos del archivo.
###
* `void establecerReferencia`: Se ocupa de establecer un valor a el atributo `referencia` cuando se quiere modificar desde afuera de los metodos de `ArchivoLecturas`.
###
* `void establecerTipoLectura`: Se ocupa de establecer un valor a el atributo `tipoLectura` cuando se quiere modificar desde afuera de los metodos de `ArchivoLecturas`.
###
* `void establecerTitulo`: Se ocupa de establecer un valor a el atributo `titulo` cuando se quiere modificar desde afuera de los metodos de `ArchivoLecturas`.
###
* `void establecerSubtema`: Se ocupa de establecer un valor a el atributo `subtema` cuando se quiere modificar desde afuera de los metodos de `ArchivoLecturas`.
###
* `void establecerDescripcion`: Se ocupa de establecer un valor a el atributo `descripcion` cuando se quiere modificar desde afuera de los metodos de `ArchivoLecturas`.
###
* `void establecerAutor`: Se ocupa de establecer un valor a el atributo `autor` cuando se quiere modificar desde afuera de los metodos de `ArchivoLecturas`.
###
* `void establecerMinutosLectura`: Se ocupa de establecer un valor a el atributo `minutosLectura` cuando se quiere modificar desde afuera de los metodos de `ArchivoLecturas`.
###
* `void establecerAnio`: Se ocupa de establecer un valor a el atributo `anio` cuando se quiere modificar desde afuera de los metodos de `ArchivoLecturas`.
###
* `string obtenerTipoLectura`: Este metodo consulta el atributo `tipoLectura` de la lectura y lo devuelve en forma de string.

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

### Metodos:

* Constructor `Menu`: Se ocupa de inicializar los atributos del objeto en texto vacio, -1, false o null.
###
* `void mostrarMenu`: Se ocupa de mostrar todas las opciones disponibles para usar el programa, recibe la opcion elegida.
###
* `void mensajeExito`: Se ocupa de mostrar por consola un mensaje de exito.
###
* `void mensajeError`: Se ocupa de mostrar por consola un mensaje de error.
###
* `void verificarOperacion`: Se ocupa de verificar que la operacion del programa sea haya llevado a cabo.
###
* `opcionUsuario`: Se ocupa de tomar la opcion elegida por el usuario y llama al metodo necesario para ejecutar esa opcion.
###
* `int obtenerOpcion`: Se ocupa de hacer una consulta a la opcion elejida por el usuario y la devuelve.

#### - Seccion menu lecturas -
* `void pedirDescripcion`: Se ocupa de pedir una descripcion para la novela historica.
###
* `void pedirSubtema`: Se ocupa de pedir al usuario un subtema y dependiendo el tipo de lectura que se este instanciando se pide un atributo diferente.
###
* `void pedirGenero`: Se ocupa de pedirle al usuario el genero de la novela.
###
* `void pedirTipoLectura`: Se ocupa de pedir al usuario el tipo de lectura que quiere crear.
###
* `void pedirDatosLEctura`: Se ocupa de pedir todos los datos necesarios para crear la lectura y completar su atributos.
###
* `void verificarEscritorAnonimo`: Se ocupa de preguntar al usuario si el autor de la lectura es anonimo.
###
* `void agregarLectura`: Se ocupa de dar de llamar a los metodos que piden los datos de la lectura y a la que da de alta a la lista de lecturas.
###
* `void quitarLectura`:  Se ocupa de pedir los datos necesarios para llamar al metodo que da de baja las lecturas en la lista.
###
* `void sortearLectura`: Se ocupa de elejir una lectura aleatoriamente.
###
* `void listarLecturas`: Se ocupa de listar las lecturas en el orden que estan guardadas.
###
* `void listarLecturasAnios`: Se ocupa de pedir al usuario los años para listar las lecturas desde y hasta los años indicados.
###
* `void listarLecturasEscritor`: Se ocupa de pedir al usuario el nombre de un autor y listar las lecturas escritas por el autor ingresado.
###
* `void mostrarGeneros`: Se ocupa de todas las opciones de generos para novela.
###
* `void listarNovelasGenero`: Se ocupa de pedir al usuario un genero de novela y listar las novelas que pertenecen al genero ingresado.

#### - Seccion menu escritores -
* `void buscarEscritor`: Se ocupa de  buscar un escritor.
###
* `void pedirDatosEscritor`: Se ocupa de pedir al usuario que ingrese los datos de un escritor y de verificar que el escritor que se intenta agregar no exista en la lista de escritores.
###
* `bool tieneANioFallecimiento`: Se ocupa de verificar si el escritor el cual se esta consultando tiene o no anio de fallecimiento.
###
* `void confirmarCambioFallecimiento`: Se ocupa de pedirle al usuario que confirme si quiere cambiar el anio de fallecimiento a pesar de que ya tenga uno existente.
###
* `void modificarAnio`: Se ocupa de pedir al usuario que ingrese el anio de fallecimiento nuevo que quiere agregar.
###
* `void modificarEscritor`: Se ocupa de pedir al usuario que ingrese el nombre y apellido del autor que quiere modificar.
###
* `void listarEscritores`: Se ocupa de listar todos los escritores de la lista.

#### - Seccion armar Cola -
* `void armarCola`: Se ocupa de instanciar una `Cola` y una `Lista` auxiliar. Tambien llama a los respectivos metodos para dar de alta lecturas en la lista auxiliar, preguntar si la lectura fue leida. Por ultimo copia la lista a la cola instanciada.
###
* `void menuLecturaLeida`: Se ocupa de preguntar al usuario si una lectura fue leida o no.
###
* `void menuCola`: Se ocupa de mostrar la cola y llama a los respectivos metodos para dar las opciones al usuario. 
###
* `void opcionesCola`: Se ocupa de mostrar al usuario  las opciones para la cola.
###
* `void salir`: se ocupa de dar un mensaje de despedida.

## Lista:
### Atributos:

* Nodo<Dato>* `primero`, `cursor`

* int `cantidad`

### Metodos:

* Constructor `Lista`: Se ocupa de inicializar los atributos de `Lista` en null o 0.
###
* Destructor `~Lista`: Se ocupa de liberar la memoria reservada durante la ejecucion del programa para las listas.
###
* `void baja`: Se ocupa de dar de baja nodos y de reapuntar los punteros con el fin de no perder los datos de la lista.
###
* `void alta`: Se ocupa de dar de alta los datos nuevos que se ingresan a la lista.
###
* `int actualizarDatoCursorAlta`: Se ocupa de pedir los datos del `cursor` segun necesite el metodo que la llama.
###
* `void altaOrdenada`: Se ocupa de hacer llamadas a los metodos que dan de alta a la lista de forma ordenada segun el anio de publicacion.
###
* `void altaComparacionInicialIgual`: Modularizacion de `altaOrdenada`. Se ocupa de efectuar el alta del nuevo dato ingresado.
###
* `void altaComapracionInicialMayor`: Modularizacion de `altaOrdenada`. Se ocupa de efectuar el alta del nuevo dato ingresado. Tambien hace llamada al metodo que da de alta en el ultimo lugar de la lista si es que es necesario.
###
* `void altaComparacionInicialMenor`: Modularizacion de `altaOrdenada`. Se ocupa de efectuar el alta del nuevo dato ingresado. Tambien hace llamada al metodo que da de alta en el primer lugar de la lista si es que es necesario.
###
* `void altaPrimerELemento`: Se ocupa de dar de alta el nuevo dato en el primer lugar de la lista.
###
* `void altaUltimoElemento`: Se ocupa de dar de alta el nuevo dato en el ultimo lugar de la lista.
###
* `int comparar`: Compara si el nuevo dato es menor o mayor al del `cursor` para realizar el alta.
###
* `void listarIntervalo`: Se ocupa de marcar desde que nodo hasta que nodo tiene cumplen los requisitos para ser mostrados por intervalo de anio.
###
* `bool elementoEncontrado`: Se ocupa de encontrar coincidencias entre anio de publicacion y titulo ingresados por el usuario y los de alguna de las lecturas existentes.
###
* `void bajaComparacionInicialIgualMenor`: Se ocupa de dar de baja una lectura segun su año de publicacion y titulo.
###
* `void bajaComparacionInicialMayor`: Se ocupa de dar de baja una lectura segun su año de publicacion y titulo.
###
* `void bajaOrdenada`: Se ocupa de hacer llamadas a los metodos que se enacargan de dar de baja elementos de una lista segun anio de publicacion y titulo.
###
* `void mostrarElementos`: Se ocupa de mostrar los elementos de una lista.
###
* `Dato consulta`: Se ocupa de obtener un nodo y devuelve sus datos.
###
* `bool vacia`: Se ocupa de preguntar si la lista esta vacia.
###
* `int obtenerCantidad`: Se ocupa de obtener la cantidad de elementos que hay dentro de la lista empezando a contar desde 1.
###
* `void apuntarCursor`: Se ocupa de apuntar el `cursor` a un nodo de la lista valido.
###
* `Dato iterarLista`: Se ocupa de iterar la lista para devolver un nodo especifico.
###
* `Dato datoPrimero`: Se ocupa de obtener el dato dentro del atributo puntero `primero`.
###
* `void reiniciarCursor`: Se ocupa de apuntar al `cursor` al primero.
###
* `Nodo<Dato>* obtenerNodo`: Se ocupa e obtener un nodo segun su posicion en la lista.

## Nodo:
### Atributos:

* Dato `dato`

* Nodo<Dato>* `siguiente`

### Metodos:

* Constructor `Nodo`: Se ocupa de inicializar los atributos en null o con el tipo de dato pasado.
###
* `void cambiarSiguiente`: Se ocupa de apuntar el siguiente l nodo recibido.
###
* `Dato obtenerDato`: Se ocupa de hacer una consulta al atributo dato de un nodo y lo devuelve.
###
* `Nodo<Dato>* obtenerSiguiente`: Se ocupa de obtener a quien apunta el puntero `siguiente` del nodo actual.

## Escritor:
### Atributos:

* string `nombreApellido`, `nacionalidad`

* int `anioNacimiento`, `aniofallecimiento`

### Metodos:

* Constructor `Escritor`: Se ocupa de inicializar los atributos con los respectivos datos del autor.
###
* Constructor `Escritor = default`: Este metodo es un costructor por default para poder usar a Escritor como Dato en los templates.
###
* `void mostrar`: Se ocupa de mostrar los datos de los autores.
###
* `void modificarFallecimiento`: Se ocupa de establecer un valor a el atributo `anioFallecimiento` cuando se quiere modificar desde afuera de los metodos de `Escritor`.
###
* `string obtenerNombreApellido`: Este metodo consulta el atributo `nombreApellido` del escritor y lo devuelve en forma de string.
###
* `string obtenerNacionalidad`: Este metodo consulta el atributo `nacionalidad` del escritor y lo devuelve en forma de string.
###
* `int obtenerAnioNacimiento`: Este metodo consulta el atributo `anioNacimiento` del escritor y lo devuelve en forma de int.
###
* `int obtenerAnioFallecimiento`: Este metodo consulta el atributo `anioFallecimiento` del escritor y lo devuelve en forma de int.

## Lectura:
### Atributos:

* string `titulo`

* int `minutos`, `anioPublicacion`

* Escritor* `autor`

### Metodos:

* Constructor `Lectura`: Se ocupa de inicializar los atributos con los respectivos datos de la lectura.
###
* Constructor `Lectura = default`: Este metodo es un costructor por default para poder usar a Lectura como Dato en los templates.
###
* Destructor `~Lectura = default`: Este metodo es un destructor por default ya que es necesario que primero se destruyan las hijas y luego la clase madre.
###
* `virtual void mostrar {}`: Este metodo es heredado por las hijas.
###
* `void mostrarAutor`: Se ocupa de mostrar los datos del autor de la lectura.
###
* `string obtenerTitulo const`: Este metodo consulta el atributo `titulo` de la lectura y lo devuelve en forma de string.
###
* `int obtenerMinutos const`: Este metodo consulta el atributo `minutos` de la lectura y lo devuelve en forma de int.
###
* `int obtenerAnioPublicacion const`: Este metodo consulta el atributo `anioPublicacion` de la lectura y lo devuelve en forma de int.
###
* `Escritor* obtenerAutor`: Este metodo consulta el atributo `autor` de la lectura y lo devuelve en forma de Escritor*.

## Cuento:
### Atributos:

* string `libro`

### Metodos:

* Constructor `Cuento`: Se ocupa de inicializar los atributos con los respectivos datos de Cuento.
###
* Destructor `~Cuento override = default`: Este metodo es un destructor por default ya que es necesario que primero se destruyan las hijas y luego la clase madre.
###
* `void mostrar override`: Se ocupa de mostrar los datos del Cuento.
###
* `string obtenerLibro`: Este metodo consulta el atributo `libro` del cuento y lo devuelve en forma de string.

## Novela:
### Atributos:

* int `genero`

### Metodos:

* Constructor `Novela`: Se ocupa de inicializar los atributos con los respectivos datos de Novela.
###
* Destructor `~Novela override = default`: Este metodo es un destructor por default ya que es necesario que primero se destruyan las hijas y luego la clase madre.
###
* `void mostrar override`: Se ocupa de mostrar los datos de la Novela.
###
* `void mostrarGenero const`: Se ocupa de mostrar el genero de la Novela.
###
* `int obtenerGenero const`: Este metodo consulta el atributo `genero` de la novela y lo devuelve en forma de int.

## NovelaHistorica:
### Atributos:

* char* `tema`

### Metodos:

* Constructor `NovelaHistorica`: Se ocupa de inicializar los atributos con los respectivos datos de NovelaHistorica.
###
* Destructor `~NovelaHistorica override = default`: Este metodo es un destructor por default ya que es necesario que primero se destruyan las hijas y luego la clase madre.
###
* `void mostrar override`: Se ocupa de mostrar los datos de la NovelaHistorica.
###
* `char* obtenerTema`: Este metodo consulta el atributo `tema` de la NovelaHistorica y lo devuelve en forma de char*.

## Poema:
### Atributos:

* int `versos`

### Metodos:

* Constructor `Poema`: Se ocupa de inicializar los atributos con los respectivos datos de Poema.
###
* Destructor `~Poema override = default`: Este metodo es un destructor por default ya que es necesario que primero se destruyan las hijas y luego la clase madre.
###
* `void mostrar override`: Se ocupa de mostrar los datos del Poema.
###
* `int obtenerVersos`: Este metodo consulta el atributo `versos` del Poema y lo devuelve en forma de int.

## Cola:
### Atributos:

* Nodo<Dato>* `primero`
* Nodo<Dato>* `ultimo`

### Metodos:

* Constructor `Cola`: Se ocupa de inicializar los atributos con los respectivos datos de Cola.
###
* Destructor `~Cola`: Se ocupa de liberar la memoria dinamica de sus elementos.
###
* `void alta`: Se ocupa de dar de alta los datos nuevos que se ingresan a la cola.
###
* `void baja`: Se ocupa de eliminar el primer Nodo de la cola, apunta el puntero primero al siguiente y si no hay mas Nodos en la cola, resetea primero a nullptr.
###
* `Dato consulta`: Se ocupa de obtener el Dato del primer elemento y lo devuelve en forma de Dato.
###
* `bool vacia`: Se ocupa de preguntar si la cola esta vacia.