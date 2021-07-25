# Unit Testing Guidelines

### 1. Mantener las pruebas unitarias pequeñas y rápidas
Lo ideal es que todo el conjunto de pruebas se ejecute antes de cada comprobación del código. Mantener las pruebas rápidas reduce el tiempo de desarrollo.

### 2. Las pruebas unitarias deberían ser completamente automatizados
El conjunto de tests se ejecuta regularmente y deberían ser automáticos para que sean útiles.

### 3. Las pruebas unitarias deben ser fáciles de correr
El conjunto de tests debe poder correrse con un simple click o un solo comando.

### 4. Medir los tests
Mediante el análisis de cobertura para poder leer la cobertura exacta de ejecución e investigar qué partes del código se ejecutan o no.

### 5. Arreglar los tests que fallan inmediatamente
Cada desarrollador debe ser responsable de asegurarse de que una nueva prueba se ejecuta con éxito en el momento del registro. Si una prueba falla como parte de una ejecución de prueba regular, todo el equipo debe dejar lo que esté haciendo y asegurarse de que el problema se solucione.

### 6. Testear siempre a nivel unitario
Tiene que haber una clase de test para cada clase y cada comportamiento debe ser testeado por separado

### 7. Empezar simple
Una prueba sencilla es mucho mejor que no hacer ninguna.

### 8. Mantener los tests independientes
Los tests nunca deben depender de otros tests o del orden de ejecución de los mismos.

### 9. Mantener los tests cerca de la clase a testear
Si la clase a testear se llama Algo, la clase de test debe llamarse AlgoTest y deben estar en el mismo paquete.

### 10. Nombrar los tests como se debe como dios manda
Asegurarse de que cada método de prueba comPRUEBA una característica distinta de la clase que se está PROBANDO y nombre los métodos de prueba en consecuencia.

### 11. Testear la API pública ¿?¿?
Las pruebas unitarias pueden definirse como clases de prueba a través de su API pública (interfaz de programación de aplicaciones). Si hay contenido privado que parece necesitar pruebas explítitas, considerar refactorizarlo en métodos públicos en clases de utilidad.

### 12. Caja negra
Testear si la clase cumple con los requisitos, como si fuéramos el cliente. Y tratar de desmenuzarla.

### 13. Caja blanca
Testear también la lógica compleja.

### 14. Testear los casos triviales también
Lo trivial es difícil de definir, puede significar cosas diferentes para personas diferentes. Los casos triviales pueden contener errores, a menudo como resultado de copy-paste.

### 15. Centrarse en la cobertura de ejecución
Esto asegura que el código se ejecute bajo algunos parámetros de entrada; la cobertura de test mejora con esto.

### 16. Testear casos borde
En números, testear negativos, 0, positivo, el más chico, el más grande, NaN, infinito, etc; para cadenas, testear cadena
vacía, no-ASCII, etc; para colecciones testear vacío, primero, último, etc. Asegurarse de que los casos borde estén cubiertos

### 17. Proveer un generador random
Para mejorar la cobertura, se pueden generar parámetros random par que los tests se ejecuten con distintas entradas cada vez.

### 18. Testear cada cosa de a una

### 19. Usar asserts explícitos
Por ejemplo, preferir assertEquals(a,b) por sobre assertTrue(a==b).

### 20. Hacer tests negativos
Son los que intencionalmente usan mal el código, verifican que sea robusto y que se esten manejando bien los errores.

### 21. Diseñar código con tests en mente
Por ejemplo, no usar demasiada herencia ni métodos virtuales públicos, reducir la API pública usando "package scope" en Java,
hacer los miembros de clase inmutables estableciendo estado en tiempo de construcción para reducir el uso de setters, etc.

### 22. No conectarse a recursos externos predefinidos
Las pruebas unitarias deben ser escritas sin conocimiento explícito del contexto del entorno en el que serán ejecutados,
para que puedan usarse en cualquier lugar y en cualquier momento.

### 23. Conocer el costo de testear
No testear es costoso y testear también lo es. En la industria se suele cubrir el código al 80%. Las áreas difíciles de testear son los errores y el manejo de excepciones cuando usamos recursos externos.

### 24. Priorizar el testeo

### 25. Preparar el código del test para fallas

### 26. Escribir tests para reproducir bugs
Cuando aparezca un bug, escribir un test que lo reproduzca y usarlo como criterio para corregir código.

### 27. Conocer las limitaciones
Las pruebas unitarias jamás pueden probar que el código sea correcto. Un test que falla indica que el código tiene errores, pero uno que pasa no prueba nada. Solo sirve para verificar y documentar los requerimientos a bajo nivel.
