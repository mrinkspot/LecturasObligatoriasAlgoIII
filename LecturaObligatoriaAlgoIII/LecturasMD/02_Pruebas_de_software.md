## Pruebas de software

### Contexto

La actividad de pruebas es parte del área de conocimiento de gestión de la calidad. Pero las pruebas no son las que confieren calidad al producto. Estas solamente **detectan errores**, y cuando los detectan, se deberá mejorar la calidad reparando el producto. Para hacer más económico el desarrollo de cualquier producto, se debe trabajar mejor, de modo tal que las pruebas, que son  una actividad de **control de calidad (QC)** sean casi siempre exitosas. Para ello, existen prácticas denominadas aseguramiento de la **calidad (QA)** que buscan mejorar el proceso de desarrollo.

> "Las pruebas pueden ser una manera efectiva de mostrar la presencia de errores, pero no hay esperanza de que sean adecuadas para mostrar su ausencia", Edsger Dijkstra.

### Qué probamos

### Verificación y validación

La **verificación** es controlar que hayamos construido el producto *tal como lo pretendimos*. La **validación** controla que lo hayamos construido *como el cliente quería*.

### Funcionalidades y atributos de calidad

Hay pruebas **centradas en probar funcionalidades**, cosas que el programa debe hacer. Estas surgen de modo natural de los requerimientos del usuario. Por ejemplo, para un TaTeTi podríamos hacer una prueba del estilo "si intento colocar una ficha en una celda ocupada, el programa debe impedirlo". Estas son **pruebas funcionales**. 

A veces debemos **probar características del sistema que no son funcionales**. Por ejemplo, "si se produce un error en el programa, el dispositivo móvil debe seguir funcionando para las demás aplicaciones". Estas son pruebas de **atributos de calidad**. Entre las pruebas de atributos de calidad, se encuentran algunas de las siguientes clasificaciones:

- Pruebas de compatibilidad: chequean las configuraciones de hardware o de red y de plataformas de software que debe soportar el producto
- Pruebas de rendimiento: evalúan el rendimiento del sistema (velocidad de respuesta, uso de memoria)
- Pruebas de resistencia o estrés: prueban el comportamiento del sistema ante situaciones que demanden muchos recursos
- Pruebas de seguridad: comprueban que sólo los usuarios autorizados puedan acceder a ciertas funcionalidades y que el programa se mantenga estable ante intentos de vulnerar su seguridad
- Pruebas de recuperación: prueban que el programa se recupere luego de una falla
- Pruebas de instalación: prueban que el sistema se pueda instalar satisfactoriamente

### Alcance de las pruebas

### Alcance de las pruebas de verificación (o técnicas)

Las **pruebas de verificación** son pruebas que los propios desarrolladores ejecutan para ver que *el programa funciona como ellos pretenden*. Se categorizan en pruebas unitarias o de integración.

Las **pruebas unitarias** *verifican pequeñas porciones de código*, como alguna responsabilidad única de un método o una única postcondición. Son pruebas ejecutadas por los programadores para ver que lo que escribieron hace lo que se pretende. La ventaja es que permiten aislarse del conjunto y analizar una pequeña porción de código. En algunos casos se usan objetos ficticios que ayuden a aislar el código, cuando dicho código precisa de otros objetos para funcionar.

Las **pruebas de integración** prueban que *varias porciones de código, trabajando en conjunto*, hacen lo que se pretende. Son pruebas que involucran varios métodos o varias clases. A veces prueban partes del sistema que se quieren aislar de otras, ya sea porque se quieren evitar accesos a redes o bases de datos o porque se quiere aislar el comportamiento. Para esto también se usan objetos ficticios.

Ambos tipos de pruebas pueden automatizarse e incluso integrarse fácilmente en los IDE, mediante herramientas como frameworks xUnit. Además suelen escribirse antes del código que prueban y se ejecutan después. Enfoques como TDD refuerzan este proceder.

Las pruebas de verificación pueden ser de caja negra o de caja blanca. Una prueba es de **caja negra** cuando la ejecutamos sin mirar el código que estamos probando. Es una prueba ciega que toma el código a probar como algo cerrado que realiza ciertas acciones bajo estímulos. 

Una prueba es de **caja blanca** cuando analizamos el código durante la prueba. Una de éstas que ha caído en desuso es la **prueba de escritorio**, mediante la cual se recorría mentalmente el código con anotaciones en papel.

Es preferible hacerlas de caja negra ya que queremos probar el funcionamiento y no la calidad de código. Las de caja blanca se usan cuando no encontramos algún error y tenemos que analizar el código en detalle; el debugging es una técnica de caja blanca.

Otra técnica de verificación de calidad de código es mediante **revisiones de código** de a dos o más programadores. No se suele hacer tradicionalmente pero es usual hacerla con ayuda de herramientas. La práctica de programar de a pares que propone Extreme Programming se enfoca en la revisión constante de código.

### Alcance de las pruebas de validación (o de usuarios)

Se suele trabajar con pruebas de aceptación diseñadas por usuarios, pero que ejecuta el equipo de desarrollo. Estas se denominan **pruebas de aceptación de usuarios (UAT)** y deben ejecutarse en un entorno lo más parecido posible al que utilizará el usuario.

Cuando un sistema debe salir a producción, se suele poner a disposición de usuarios reales. Si las pruebas se hacen en un entorno controlado por el equipo de desarrollo, se llaman **pruebas alfa**. Si el producto se deja a disposición del cliente, en su entorno, se llaman **pruebas beta**.

Cuando probamos solamente comportamiento, es decir, que la *lógica de la aplicación sea correcta* pero sin interfaz de usuario, hacemos **pruebas de comportamiento**. Se centran en el comportamiento del sistema y la cooperación de los usuarios es importante. 

### Pruebas en producción

También puede ponerse el sistema en producción y esperar a ver qué errores surgen o qué problemas encuentran los usuarios. Es un enfoque deshonesto y esto suele ser muy costoso. Sin embargo, en aplicaciones cuyos errores no causen grandes riesgos, es una opción.

### La pirámide de pruebas y sus razones

![image-20210725190121221](C:\Users\barto\AppData\Roaming\Typora\typora-user-images\image-20210725190121221.png)

- Las pruebas unitarias se ejecutan más rápido que las de integración. Entre más abajo de la pirámide, más rápido se ejecutan: se pierde menos tiempo esperando y se logra mantener la concentración de los desarrolladores.
- Las pruebas de aceptación son más frágiles que las de comportamiento, pues dependen de la interfaz de usuario, que suele ser cambiante; a mayor fragilidad, mayor tiempo gastado en mantenimiento de pruebas.

**Corolario:** si una prueba falla, puede deberse a que no se probó algo correctamente en ese nivel o en el nivel de abajo.

### Roles del desarrollo ante las pruebas

### Visiones tradicionales

Sostiene que debe haber personas con el rol de programadores y otras con el rol de testers. Los testers ejecutan las pruebas y velan porque el producto llegue sin errores a los clientes, deben ejecutar pruebas de aceptación en un ambiente especial y sólo ellos pueden autorizar la liberación del producto para su entrega. La calidad sigue siendo introducida por los programadores.

### La visión ágil

La responsabilidad por entregar un producto de calidad y sin errores pasa a ser de todo el equipo de desarrollo.

### Pruebas automatizadas: quién las desarrolla

- Las pruebas unitarias las deben escribir y ejecutar los programadores
- Las pruebas de integración conviene que las escriban los programadores y las ejecuten sobre servidores de integración
- Las pruebas de comportamiento pueden ser desarrolladas por cualquier rol
- Las UAT deben escribirlas los usuarios o analistas de negocio, pero podrían escribirlas los testers.

### Pruebas manuales: quién diseña la prueba

Hoy en día se suelen dejar como pruebas manuales algunos tipos de UAT que luego ejecutarán testers y clientes.

### Pruebas y desarrollo

### Cuándo probamos

Al principio del desarrollo de software, las pruebas se ejecutaban como última etapa del desarrollo de un proyecto. En los años 90, con el auge de los procesos iterativos, se empezó a probar al final de cada iteración. En los años 2000, los métodos ágiles proponían la prueba continua y automatizada, haciendo que las pruebas guiaran el proceso de desarrollo. Hoy en día, con el surgimiento de ciclos de flujo continuo, las pruebas son continuas a lo largo de todo el desarrollo.

Cada vez que se incorporan nuevas características al programa, podemos provocar que dejen de funcionar cosas que ya habían sido probadas, es decir, una **regresión**. Para evitarlas, se ejecutan cada tanto **pruebas de regresión**, que es ejecutar las pruebas de todo el sistema a intervalos regulares.

### Ventajas de la automatización

- Nos independizamos del factor humano, con su carga de subjetividad y variabilidad.
- Es más fácil repetirlas y es aplicable a regresiones, debugging y errores provenientes del sistema.
- Las pruebas en código sirven como herramienta de comunicación.

### Tipos de prueba y automatización

![image-20210725191726051](C:\Users\barto\AppData\Roaming\Typora\typora-user-images\image-20210725191726051.png)



### TDD

Fue la primera práctica basada en automatización de pruebas que estuvo bien soportada por herramientas. La presentó Kent Beck en el marco de Extreme Programming. Incluye tres sub-prácticas:

- Automatización: las pruebas del programa deben ser hechas en código y con la sola ejecución del código de pruebas debemos saber si funciona bien o mal
- Test-First: las pruebas se escriben antes del código a probar
- Refactorización posterior: para mantener la calidad de código, se lo cambia sin cambiar la funcionalidad

TDD denomina pruebas a las pruebas unitarias.

![image-20210725193715460](C:\Users\barto\AppData\Roaming\Typora\typora-user-images\image-20210725193715460.png)

Las ventajas de TDD son:

- Las pruebas sirven como documentación del uso esperado de lo que se está probando
- Las pruebas escritas con anterioridad ayudan a entender  mejor lo que se está por desarrollar
- Las pruebas escritas con anterioridad suelen incluir más casos de pruebas negativas
- Las pruebas escritas con anterioridad minimizan el condicionamiento del autor por lo ya construido y da más confianza al programador sobre el hecho de que el código que escribe siempre funciona
- Las pruebas escritas con anterioridad permiten especificar el comportamiento sin restringirse a una única implementación
- La automatización permite independizarse del factor humano y facilita la repetición de las pruebas
- La refactorización constante facilita el mantenimiento de un buen diseño

### Pruebas orientadas al cliente

Cuando Kent Beck presentó Extreme Programming, hizo hincapié en especificar mediante historias de usuario acompañadas por pruebas de cliente. Esto ha minimizado la importancia de las pruebas de aceptación. Con el tiempo, fueron surgiendo algunas prácticas que buscaron subsanar este problema: BDD, STDD, ATDD, SBE. Estas cuatro prácticas sirven tanto como especificaciones del usuario, guías para el desarrollo y casos de aceptación a probar.

### Integración y entrega continuas

La **integración continua** (IC) surge a partir de las recomendaciones de Kent Beck. La idea es facilitar y automatizar al máximo las integraciones antes de liberar el producto que se está desarrollando. Consiste en realizar la compilación, construcción y pruebas del producto en forma sucesiva y automática como parte de la integración. Las integraciones deben terminar siempre en el tronco principal de la herramienta de control de versiones y se presume que están libres de errores. Como una derivación de CI, surgió la práctica de **entrega continua** (CD). Mientras que en CI la línea de automatización termina con una integración en el ambiente de desarrollo, CD pretende que el código siempre esté en condiciones de ser desplegado en el ambiente productivo, por lo tanto, debemos incluir todas las pruebas de aceptación que se pueden automatizar. 

Hay una técnica llamada **despliegue continuo** que pretende que se esté permanentemente en condiciones de desplegar y que efectivamente cada pequeño cambio se despliegue en el ambiente de producción.

Con estas prácticas se disminuye el riesgo de la aparición de errores en las pruebas.

### ¿Cómo se diseña una prueba?

### Diseño de pruebas unitarias y técnica en general

Para las pruebas unitarias, preferentemente hay que hacer pruebas de caja negra porque buscamos probar el funcionamiento, no deberíamos pensar en la implementación específica. 

Una forma de probar es ponernos en el rol de quien usa el módulo a probar, en el caso de las unitarias sería el mismo programador. Seguimos las nociones del diseño por contrato: establecemos pre y postcondiciones. Con las pre, obtenemos casos de excepción y con las post las posibles salidas. Cada postcondición debería definir al menos una prueba.

### Diseño de pruebas de cliente

Si la prueba debe chequear un requisito del cliente, y dado que éste debe colaborar en escribirla, es bueno usar la técnica de especificar con ejemplos. Al menos tiene que haber una prueba para el escenario típico, una para cada flujo de excepción y una para cada flujo alternativo.

### Cobertura

Es el grado en que los casos de pruebas de un programa llegan a recorrerlo al ejecutar las pruebas. Se la suele denominar "cobertura de pruebas" o "cobertura de código". Se usan como una medida de la calidad de las pruebas: a mayor cobertura, las pruebas del programa son más exhaustivas, y por lo tanto existen menos situaciones que no están siendo probadas. *La cobertura sólo mide la calidad de las pruebas, no confundir con la calidad del programa*. El nivel de cobertura no debería guiar el desarrollo. Una buena idea es usar las métricas de cobertura para observar tendencias.

Un objetivo razonable es llegar a un **80% o 90%** en métricas como las de sentencias, ramas y combinada de ramas y condiciones. Las zonas de mayor criticidad requerirán un grado de cobertura mayor, cercana al 100%.







