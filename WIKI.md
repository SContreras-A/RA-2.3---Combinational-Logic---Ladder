# RA-2.2 - COMBINATIONAL LOGIC IN LADDER

<img width="1351" height="759" alt="image" src="https://github.com/user-attachments/assets/981ced07-9997-43d4-967e-020b824b3566" />

## 1. ANÁLISIS DEL PROBLEMA

El problema consiste en supervisar el nivel de un tanque de líquido utilizando un sistema automático basado en sensores. Para esto, se cuenta con tres entradas (B1, B2 y B3), que corresponden a sensores ubicados en diferentes alturas del tanque. Cada uno de estos sensores indica si hay o no presencia de líquido en su posición, permitiendo así conocer el nivel del contenido dentro del tanque.

El sensor B1 está ubicado en la parte inferior y detecta niveles mínimos, B2 se encuentra en una posición intermedia y representa un nivel adecuado de operación, y B3 está en la parte superior e indica cuando el tanque está cerca de llenarse completamente. A partir de la combinación de estos sensores, es posible determinar el estado del sistema.

Las salidas (H1, H2, H3 y H4) corresponden a indicadores luminosos que muestran de forma sencilla el estado del tanque. Por ejemplo, H4 se activa cuando el tanque está vacío, H2 cuando el nivel es bajo, H1 cuando el nivel es adecuado y H3 cuando el nivel es alto. Esto permite que cualquier usuario pueda interpretar fácilmente la condición del tanque sin necesidad de analizar directamente las señales de los sensores.

Además, el sistema incluye una salida adicional (H5) que indica una condición de error. Esta se activa cuando los sensores presentan combinaciones que no tienen sentido físico, como detectar líquido en un sensor superior mientras uno inferior está desactivado. Este tipo de situaciones suele indicar una falla en los sensores o en la medición.

Es importante resaltar que el estado en el que todos los sensores están desactivados no se considera un error, ya que simplemente indica que el tanque está vacío. En conjunto, el sistema no solo permite monitorear el nivel del líquido, sino también detectar posibles fallas, lo que lo hace más confiable y útil en aplicaciones reales.

## 1.1. TABLA DE VERDAD

Una vez definidas las variables de entrada y salida del sistema, se procede a la elaboración de la tabla de verdad, la cual permite establecer las combinaciones válidas de los sensores y determinar el comportamiento esperado del sistema ante cada posible estado.

<img width="728" height="411" alt="image" src="https://github.com/user-attachments/assets/be04059b-dbfc-4555-af44-42499a88ad67" />


## 2. IMPLEMENTACIÓN EN CODESYS

Una vez construida la tabla de verdad completa, se procede a la simulación del sistema en el entorno de CODESYS. Esta etapa permite validar el comportamiento del modelo implementado, verificando que las salidas respondan correctamente ante cada combinación de entradas definida previamente. De esta manera, se asegura la coherencia entre el diseño lógico y su ejecución práctica dentro del entorno de simulación.

### 2.2. CREACIÓN DE VARIABLES

Se realiza la declaración de las variables en el entorno de programación, asignando nombres representativos a cada una de ellas según su función dentro del sistema. Posteriormente, se verifica su correcta creación mediante su visualización en formato de tabla, lo que permite confirmar tanto su tipo como su disponibilidad para su uso en la lógica del programa.

| CÓDIGO DE DECLARACIÓN | FORMATO DE TABLA |
| :--- | :---: |
| <img width="293" height="307" alt="image" src="https://github.com/user-attachments/assets/3b00b0ad-45c7-42c8-8a07-e54efc4106bc" /> | <img width="703" height="244" alt="image" src="https://github.com/user-attachments/assets/b2e2f3c4-90fe-4c59-98f0-86532e116d2f" /> |

### 2.3. IMPLEMENTACIÓN DE TABLA DE VERDAD EN FORMATO DE LADDER EN CODESYS

Con las variables de entrada y salida previamente definidas, se procede a implementar los distintos casos establecidos en la tabla de verdad mediante el uso del lenguaje Ladder (LD) en CODESYS. A través de esta representación gráfica, se construyen las redes lógicas que permiten asociar cada combinación de entradas con su respectiva salida, facilitando así la comprensión y validación del comportamiento del sistema.

| CASOS DE NIVEL DEL TANQUE | ERROR DE SENSOR |
| :---: | :---: |
| <img width="846" height="694" alt="image" src="https://github.com/user-attachments/assets/1e8726df-ebd9-43e1-8914-914a4d083114" /> | <img width="860" height="500" alt="image" src="https://github.com/user-attachments/assets/aa83b507-b7c7-4f15-a99f-ec2f736e3649" /> |

### 2.4. VISUALIZACIÓN CODESYS

Se implementa una interfaz de visualización para la simulación con el fin de facilitar la comprensión del comportamiento del sistema. En esta interfaz, se utilizan interruptores tipo ON/OFF que representan el estado de los sensores de nivel, así como lámparas de distintos colores que simbolizan los indicadores luminosos (LED) asociados a cada condición del tanque.

Esta representación permite observar de manera clara e intuitiva cómo cambian las salidas del sistema en función de las entradas, mejorando la interpretación y el análisis del funcionamiento del modelo.

<img width="564" height="671" alt="image" src="https://github.com/user-attachments/assets/13549951-f1ea-4065-a7fd-bc6692821bd4" />

Se evidencian los siguientes cambios:

| TANQUE VACÍO | TANQUE NIVEL BAJO | TANQUE EN NIVEL ÓPTIMO | TANQUE LLENO |
| :---: | :---: | :---: | :---: |
| <img width="591" height="708" alt="image" src="https://github.com/user-attachments/assets/35549679-3420-4eb5-b46d-889aac642ea0" /> | <img width="599" height="666" alt="image" src="https://github.com/user-attachments/assets/d749b63b-9766-4690-95c7-b21f1b96ddb5" /> | <img width="543" height="664" alt="image" src="https://github.com/user-attachments/assets/5ce2e929-e202-4ad4-8d01-c38eab96364c" /> |<img width="612" height="682" alt="image" src="https://github.com/user-attachments/assets/1f27bb55-08e9-44df-b953-74247aadbaaf" /> |

Adicionalmente se manejan los errores de sensor de la siguiente manera:

| ERROR (1-0-1) | ERROR (1-1-0) | ERROR (0-1-0) | ERROR (1-0-0) |
| :---: | :---: | :---: | :---: |
| <img width="569" height="668" alt="image" src="https://github.com/user-attachments/assets/eefa7432-0e26-4bc8-a79a-99b8092751ba" /> | <img width="570" height="676" alt="image" src="https://github.com/user-attachments/assets/867db50a-f1b0-406c-b49b-44cae860e358" /> | <img width="569" height="666" alt="image" src="https://github.com/user-attachments/assets/3e099742-9a76-436e-a0a8-725c7cbc130f" /> | <img width="573" height="674" alt="image" src="https://github.com/user-attachments/assets/7ca2e9fb-8694-4ae6-bc89-218775c84f79" /> |

## 3. IMPLEMENTACIÓN EN OPENPLC

Una vez validado el correcto funcionamiento de la simulación y la visualización en el entorno de CODESYS, se procede a replicar la lógica del sistema en el software OpenPLC. Este paso permite adaptar el diseño a un entorno compatible con hardware embebido, con el objetivo de realizar su posterior implementación en una plataforma Arduino, facilitando así la integración entre el modelo desarrollado y su aplicación en un sistema físico. 

### 3.1. CREACIÓN DE VARIABLES 

Se replica el proceso de declaración de variables previamente realizado en CODESYS; sin embargo, en este caso se lleva a cabo en formato de tabla dentro de OpenPLC, incluyendo su respectiva documentación. Esto permite una organización más clara de las variables, facilitando su identificación, asignación y comprensión dentro del sistema.

<img width="1439" height="399" alt="image" src="https://github.com/user-attachments/assets/b01901fb-a679-44bd-8cef-287cda7f86bc" />

### 3.2. PROGRAMACIÓN DE SISTEMA EN LADDER

Con las variables ya definidas, se procede a implementar los mismos casos establecidos previamente en CODESYS, replicando la lógica del sistema en OpenPLC. Este proceso permite verificar que el comportamiento del modelo se mantenga consistente entre ambas plataformas, validando así su correcto funcionamiento antes de su implementación en hardware.

| NIVEL DEL TANQUE | ERROR DE SENSOR |
| :---: | :---: |
| <img width="712" height="875" alt="image" src="https://github.com/user-attachments/assets/18901c95-a9a8-4280-bd8a-fe985757f1b3" /> | <img width="739" height="520" alt="image" src="https://github.com/user-attachments/assets/d22ee7f1-95b9-4769-a95b-6520d45908af" />| 


### 3.3. SIMULACIÓN EN CODESYS

Con el sistema ya programado, se procede a ejecutar la simulación del modelo desarrollado, con el fin de verificar su correcto funcionamiento. Durante esta etapa, se comprueba que las salidas respondan adecuadamente ante las diferentes combinaciones de entradas, asegurando así la coherencia y validez del sistema implementado.

| TANQUE VACÍO | TANQUE NIVEL BAJO | TANQUE EN NIVEL ÓPTIMO | TANQUE LLENO |
| :---: | :---: | :---: | :---: |
| <img width="728" height="227" alt="image" src="https://github.com/user-attachments/assets/f9b55619-c720-4b2d-87c4-55f0a7cafa3e" /> | <img width="743" height="226" alt="image" src="https://github.com/user-attachments/assets/c3be650f-7f23-4a71-960e-d09c59829128" /> | <img width="719" height="218" alt="image" src="https://github.com/user-attachments/assets/6b6ea6ae-5700-495f-94a4-b5dfdb9ce7e7" /> | <img width="730" height="223" alt="image" src="https://github.com/user-attachments/assets/edd3ab29-9793-40f0-902c-8d76503d492e" /> |

De la misma manera, se modelan las condiciones de error del sistema, considerando aquellas combinaciones de entradas que no son físicamente coherentes. Esto permite integrar mecanismos de detección de fallas dentro de la lógica implementada, garantizando una respuesta adecuada ante posibles inconsistencias en las señales de los sensores.

| ERROR (1-0-1) | ERROR (1-1-0) | ERROR (0-1-0) | ERROR (1-0-0) |
| :---: | :---: | :---: | :---: |
| <img width="714" height="502" alt="image" src="https://github.com/user-attachments/assets/c72d2681-daa1-488a-8852-1b11469f8e7e" /> | <img width="737" height="521" alt="image" src="https://github.com/user-attachments/assets/e60b5a4d-5a10-4776-8006-a1ad2215c174" /> | <img width="721" height="495" alt="image" src="https://github.com/user-attachments/assets/50f71f21-c954-46d0-af0e-1dfee2408be8" /> | <img width="723" height="502" alt="image" src="https://github.com/user-attachments/assets/bb247150-6aeb-4c7a-bc48-dfda309a0b83" /> |

## 4. PRUEBAS ELECTRÓNICAS FÍSICAS

Una vez validado el correcto funcionamiento de la simulación, se procede a iniciar la fase de pruebas en físico. En esta etapa, se implementa el sistema en el hardware seleccionado, con el fin de comprobar su comportamiento en condiciones reales y verificar que los resultados obtenidos en la simulación se reproduzcan adecuadamente en la práctica.

### 4.1. MAPEO DE VRIABLES EN OPENPLC

Con las variables definidas en el software OpenPLC, se procede a seleccionar la plataforma de implementación, optando en este caso por una placa Arduino Uno. Posteriormente, se realiza el mapeo de las variables de entrada y salida hacia sus respectivos pines digitales, estableciendo así la conexión entre la lógica del programa y el hardware físico.

| MAPEO DE PINES | UBICACIÓN DE VARIABLES |
| :---: | :---: |
| <img width="707" height="445" alt="image" src="https://github.com/user-attachments/assets/1942bf43-aab3-4901-886d-b7dd8393419d" /> | <img width="1500" height="552" alt="image" src="https://github.com/user-attachments/assets/e06dbe70-3cc3-4e84-bcf6-6892f4838c51" /> |

 ### 4.2. SIMULACIÓN ESPACIO FÍSICO

Una vez realizado el mapeo de los pines digitales del Arduino, se procede a compilar el sistema y cargar el programa en la placa Arduino Uno previamente conectada. Este proceso permite transferir la lógica desarrollada en OpenPLC al dispositivo físico, habilitando así la ejecución del sistema en un entorno real. El funcionamiento obtenido se evidencia en el registro videográfico presentado a continuación, el cual muestra tanto la operación del sistema como el desarrollo completo de la solución.








