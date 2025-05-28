# ProyectoProgramacionAvanzada
Este repositorio es para nuestro proyecto de programacion avanzada en el grupo humildad: Ivan Santiago Lastra, Ana murcia, Lucas Fuentes y Martin Sanmiguel 

1era parte README C++


Este proyecto implementa un pipeline ETL (Extract, Transform, Load) en C++ para procesar un
archivo CSV alojado local de admisiones universitarias. Su objetivo es extraer datos
académicos de 400 estudiantes, transformarlos mediante operaciones de análisis estadísticos
interactivos, y finalmente la información en dos formatos:
- Un informe de texto (.txt) con los resultados de las estadísticas.
- Un archivo binario estructurado con un encabezado (número de registros) y registros
tipo Student.
Al ejecutarse, el diseño modular distribuye automáticamente una copia del CSV al espacio de
trabajo de cada estudiante en el servidor.
1. Requisitos:
○ Compilador C++ compatible con C++11 o superior.
○ Archivo de configuración ".env" con las variables necesarias.
2. Instrucciones para Compilar:
 Asegúrese de tener las librerías <libssh2.h> y <libssh2_sftp.h> instaladas y
accesibles.
 En la consola de su compilador ejecute:
“g++ -std=c++11 -o etl_pipeline main.cpp”
 Verifique que no haya errores de compilación.
3. Instrucciones para Ejecutar:
 Coloque el archivo .env en el mismo directorio del ejecutable.
 En consola ejecute:
“./etl_pipeline”
 El programa realizará la lectura y carga del CSV en una estructura de matriz
dinámica (CsvMatriz). También se crea el archivo binario
“Admission_Predict_new.bin” con un encabezado con el número de filas igual a
la cantidad de estudiantes, y el número de columnas igual a los datos por cada
estudiante. Luego se valida la creación correcta, dimensiones y primeros
registros del archivo binario. Por último, se presenta un menú interactivo para:
i. Mostrar información general del dataset.
ii. Ver las 5 primeras filas.
iii. Generar estadísticas descriptivas (media, mediana, desviación, rango).
iv. Mostrar matriz de correlaciones.
v. Salir.
 La exportación de las estadísticas y resultados se realiza al archivo
‘transformacion_resultados.txt’.
4. Estructura del Código:
 Estructuras principales:
i. Struct Student: Representa un registro binario estructurado. Contiene
campos como greScore, toeflScore, universityRating, sop, lor, cgpa,
research y chanceOfAdmit, que contienen los valores relevantes del
archivo de entrada y el resultado.

ii. Struct CsvMatriz: Implementa una matriz dinámica tridimensional para
representar el contenido del archivo CSV. Esta permite el
almacenamiento y manipulación de filas, columnas y celdas individuales.
 Funciones de gestión de la matriz:
 
i. Función crearMatriz: Inicializa una matriz con una capacidad predefinida.

ii. Función redimensionarMatriz: Ajusta dinámicamente el tamaño de la
matriz si se supera su capacidad.

iii. Función leerCSV: Lee el archivo línea por línea, y llena la estructura
CsvMatriz con sus valores.

iv. Función liberarMemoriaCsvMatriz: Asegura la correcta liberación de
memoria al terminar la ejecución.

 Funciones de análisis de datos:
i. Función esNumerico: Comprueba si una cadena representa un valor
numérico válido.

ii. Función generarEstadisticas: Se encarga de calcular las medidas
estadísticas descriptivas para cada columna numérica. Además de
mostrarse en pantalla, estas estadísticas se exportan automáticamente al
archivo de texto ‘transformacion_resultados.txt’.

iii. Función calcularCorrelacion: Implementa el coeficiente de correlación
entre dos vectores.

iv. Función mostrarCorrelaciones: Genera una matriz de correlaciones entre
todas las columnas numéricas del dataset original.

Funciones de presentación e interacción con el usuario:
i. mostrarMenu: Muestra las opciones disponibles al usuario.

ii. mostrarInformacionGeneral: Muestra el número de filas y columnas, al
igual que los encabezados.

iii. mostrarCabecera: Imprime las primeras 5 filas del dataset.
 Funciones de archivos binarios:
 
i. procesarYGuardarBinario: Convierte los datos de la matriz a un archivo
binario. Primero escribe el encabezado con las dimensiones de la matriz
y luego cada celda serializada. Luego, realiza una validación leyendo los
primeros registros y mostrando los encabezados y contenido para
confirmar la correcta creación del archivo.

 Funciones de archivos txt:
i. Función enviarEstadisticasTxt: Esta función se encarga del proceso de
creación y edición del archivo ‘transformacion_resultados.txt’. Primero, el
archivo se abre en modo escritura. Luego el programa recorre cada
columna del dataset, validando que los datos sean numéricos. Si la
columna es válida, se calculan las estadísticas descriptivas del dataset,
para luego ser escritos dentro del mismo archivo. Finalmente, se cierra el
archivo para asegurar que todos los datos hayan sido guardados
correctamente. En caso de errores durante la escritura, el sistema genera
un mensaje de advertencia por medio de la consola. Dado que es un
archivo de texto, el usuario puede abrirlo y editarlo en caso de que quiera
añadir, eliminar o modificar los datos o alguna información adicional.

Función main: Actúa como coordinador principal del desarrollo del código y del
proceso ETL. Carga el archivo CSV desde el disco, ejecuta el procesamiento
binario, abre el menú interactivo para permitir al usuario consultar estadísticas, y
por último libera la memoria ocupada por la matriz.

6. Diseño:
Las funciones están separadas por bloques bien delimitados, lo que facilita su
lectura y modificación. Para adaptar el sistema a otros datasets, solo sería
necesario ajustar la ruta del archivo de entrada, y si es necesario, adaptar la
estructura Student a los nuevos campos.
7. Mantenimiento y Validación:
Para añadir nuevas métricas o formatos de salida, basta con extender los
módulos de transformación o carga. Cada módulo puede probarse de forma
aislada usando casos de prueba unitarios.
8. Distribución Automática de CSV:
 Como salida, el sistema genera dos archivos clave. El primero es
‘Admission_Predict_new.bin’, que contiene los registros almacenados en formato
binario. El segundo es ‘transformacion_resultados.txt’, que incluye un informe
legible con los indicadores estadísticos del dataset.



README JAVA:


Se muestra en este readme la distribucion de clases realizadas para su funcionalidad dados el JSON extraido del binario de C++ de la logica establecida en la estructura student y su respectivo diseño
En la clase main primero se importan diversas librerías con funciones como leer archivos JSON, construir interfaces y todos sus elementos(Color, front, layout y el click del mouse). Usando SwingUtilities se inicia la interfaz gráfica de la ventana de admisiones, y en el método estático crearVentana se usa Jframe para instanciar el simulador de admisiones, el tamaño de la ventana y la función de terminar el programa al cerrar la ventana. 

Se carga la imagen de fondo(galaxia) usando Jlabel e ImageIcon, se reemplaza el fondo predeterminado de la interfaz(blanco) por el fondo seleccionado usando setContentPane y se aplica un GridLayout(cuadricula) para facilitar la organización de los elementos gráficos de la ventana.

Usando JTextField se crean los campos de textos en los que el usuario inserta los datos y más adelante se define un fondo blanco en estos campos para generar contraste y una buena visibilidad de los datos que insertó el usuario usando setForeground(Color.WHITE). 

Luego se crea el botón para calcular la predicción con JButton, el texto que indica la probabilidad de admisión con los datos insertados con JLabel y se ajustó la estética del botón usando setForeground, setBackground, setOpaque y setBorderPainted, que transforman este elemento a letra blanca, fondo gris sin borde y con el fondo visible. Y se agregan a la ventana en el GridLayout.

Luego se define la acción al hacer click en el botón usando addActionListener y  un try y catch. Primero se lee el archivo Json y lo ajusta a java mediante el objeto “Datos” y cierra el archivo. A continuación muestra los coeficientes en la consola y recibe los valores ingresados por el usuario convirtiendolos de texto a  valores de double usando Double.parseDouble(---Field.getText()).  

Finalmente aplica la fórmula de regresión lineal donde cada valor ingresado por el usuario se multiplica por el peso asignado a la variable en el archivo Json y se suman todos los resultados, el resultado final se asigna a una variable double z que se usará más adelante para determinar si la ventana generada es de aprobación o no y se muestra en la interfaz con 2 decimales. Al final se aplica la excepción en caso de un error en los datos o al leer el archivo Json y se imprime un mensaje de error en la consola. Finalmente se llama a ResultadoVentana para mostrar el resultado.

En la clase ResultadoVentana se crea el método estático mostrarResultado que recibe la variable z definida en el main, usando JFrame se crea una nueva ventana, usando setLocationRelativeTo(null) se ubica en la mitad de la pantalla y nuevamente se define la función de terminar el programa si se cierra la ventana ventana usando setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE).

 Después se crea el espacio para la imagen y texto y usando un condicional if-else se define la imagen del resultado*(Aprobado/No aprobado), si el resultado, que esta definido en z es más de 0.8035 es aceptado, de lo contrario no es aceptado. Finalmente se define la imagen usando ImageIcon, el tamaño con getScaledInstance,  el posicionamiento del texto que la acompaña y se hace visible la ventana con setVisible.

En la clase Datos se guarda el contenido del archivo Json en variables double y crea una variable de tipo coeficiente que contiene todos estos valores para usarlos en la clase Main. Especificamente en la linea Datos pesos = gson.fromJson(new FileReader("modelo.json"), Datos.class); donde lee coefficients e instancia un objeto de tpo Coeficientes, que asigna a pesos.coeficientes. Desde ahí se accede a pesos.coefficients.gre y todas las otras variables del archivo Json.

En la clase Coeficientes se definen los pesos de cada variable, es decir, el número que se multiplica con el que ingresó el usuario en la regresión lineal, deserializando usando la librería SerializedName para identificar las variables. Esta librería mapea los  nombres del archivo JSON y los transforma a los nombres de las variables en una clase Java.


