## The Art of Enbugging

### Intro

Enbugging: "poner" bugs en el código. Podemos establecer condiciones que nos harán poner bugs en algún momento. Una forma de prevenir esto, es mantener una apropiada "separación de intereses", o sea, diseñar el código de manera tal que las clases y módulos tengan responsabilidades claras, bien definidas y aisladas; todo esto puede ser complejo de hacer. El objetivo principal es escribir código "tímido", código que no revele mucho de sí mismo a nadie más ni que hable con otros más de lo necesario. El código tímido nunca mostrará sus "privacidades" a "amigos".

### Tell, don't ask

Una distinción del código orientado a objetos es la idea de emitir un comando a una entidad para hacer algo. Esto se ve explícitamente en Smalltalk o Ruby, donde la invocación de métodos se ve como mensajes pasándose a través de objetos, y no como llamadas a funciones. Es la metáfora de pasar mensajes. 

Hay una distinción importante entre el código de procesos y el de objetos: la programación por procedimientos tiende a obtener información y luego tomar decisiones basándose en ella. El código orientado a objetos le dice a los objetos que hagan cosas. Le envias comandos al objeto diciéndole lo que querés que hagan. No queremos preguntarle explícitamente a un objeto cual es su estado, tomar uan decisión y luego decirle al objeto qué hacer. 

No debemos tomar decisiones basandonos en el estado del objeto y luego cambiarlo. Eso es responsabilidad del objeto, no nuestra. Tomar decisiones fuera del objeto viola el encapsulamiento y puede generar futuros bugs. Queremos decirle a los objetos qué hacer, no preguntarles sobre su estado. 

Es bueno categorizar los métodos como un comando o como una consulta. El comando cambiará el estado del objeto y puede devolver algún valor útil. Una consulta solamente da información sobre el estado del objeto. Esta separación mantiene el código "tímido"; el que invoca no sabe mucho sobre cómo el comando se ejecutará.

### The pretty good idea of Demeter

No solo buscamos decir lo menos posible a otros objetos, también buscamos hablar con la menor cantidad de objetos posible. 

Una herramienta útil para aplicar acá es "la Ley de Demeter para funciones". Esta ley sugiere que un objeto sólo debe llamar:

- a sí mismo,
- a cualquier parámetro que se le pasa en el método,
- a cualquier objeto que haya creado,
- a cualquier objeto componente que se mantenga directamente

En el siguiente ejemplo, el acceso directo extiende el acoplamiento, 

```java
my_television.front_panel.switches.power.on();
```

pues quien invoca sabe que una Television tiene un panel frontal, este panel tiene unos interruptores, uno de esos es "power" y éste tiene un método "on" que enciende la tele. En vez de preguntar toda esa información, es mejor decirle a la tele qué hacer:

```java
my_television.power_up();
```

Y así el invocador no tiene conocimiento del estado interno del objeto. Esta llamada de más alto nivel suena más como un requerimiento de usuario, y menos como un detalle de implementación, lo cual significa que estamos programando más cerca al domino del problema.

La desventaja de esto es que al final estamos escribiendo métodos wrapper que delegan y nada más. El costo es ineficiencia versus acoplamiento. El acoplamiento no es aceptable porque aumenta las chances de que un cambio rompa algo en otro lugar. Pero en algunos casos puede ser que la velocidad sea muy importante y que el acoplamiento sea aceptable.