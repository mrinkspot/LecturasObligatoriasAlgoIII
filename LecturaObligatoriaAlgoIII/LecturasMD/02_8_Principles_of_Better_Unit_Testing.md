## 8 Principles of Better Unit Testing

### ¿Qué hace que una prueba unitaria sea buena?

Debe ser corta, rápida y automatizada, y debe testear que una parte específica del programa funcione. Prueban una funcionalidad particular de un método o clase y deben tener una condición clara para que pase o falle. Con estas pruebas, nos aseguramos de que el código funcione. Un buen test sólo falla cuando se introduce un nuevo bug y debe ser fácil de entender por qué falló.

### Guideline #1: saber lo que estás testeando

Un test escrito sin un claro objetivo suele ser largo, difícil de entender y por lo general testea más de una cosa. Un truco es ponerle al test el nombre del escenario a testear y el resultado esperado. Testear una sola cosa hace que un test sea más fácil de leer y es más fácil entender por qué falla.

### Guideline #2: las pruebas unitarias deben ser autosuficientes

Una buena prueba unitaria debe estar aislada. Evitar las dependencias.

### Guideline #3: las pruebas deben ser determinísticas

Una prueba debería o siempre pasar o siempre fallar. Hay que evitar escribir tests con inputs random.

### Guideline #4: convenciones de nombre

Si está bien nombrado, se entiende más rápido qué se testea y por qué falla.

### Guideline #5: repetirse

Evitar los duplicados en los tests hace que estos sean más difíciles de leer y entender.

### Guideline #6: testear resultados, no implementaciones

Un buen test fallaría solo en caso de un error o de un cambio de requerimiento.

### Guideline #7: evitar la sobreespecificación

Usualmente escribir tests muy precisos los convierte en tests frágiles. Por ejemplo, hay que evitar hacer un test que pruebe que un método se llama exactamente n veces. Se pueden  usar frameworks de aislamiento para establecer un comportamiento por default de un objeto externo.

### Guideline #8: usar frameworks de aislamiento

O sea, usar mocks.