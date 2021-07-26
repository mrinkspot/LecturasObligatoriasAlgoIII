## Replace conditional with Polymorphism

### Problema

Tenemos un condicional que hace varias cosas dependiendo del tipo de objeto o propiedades.

### Solución

Crear subclases que coincidan con las ramas del condicional. En ellas, crear un método compartido y mover el código de la rama a éste. Luego reemplazar el condicional con la llamada al método. El resultado es una implementación lograda a través del polimorfismo.

### Por qué refactorizar

Esta técnica ayuda si el código está haciendo varias cosas que varían basadas en:

- la clase del objeto o interface que implementa
- el valor de un atributo del objeto
- el resultado de llamar un método del objeto

### Beneficios

- Cumple el principio de Tell don't Ask
- Elimina el código duplicado
- Si se requiere agrega una nueva variante, solo hay que agregar una nueva subclase sin modificar el código existente (open/closed principle)

### Cómo refactorizar

Debemos tener una jerarquía de clases que contenga comportamientos alternativos. Otras técnicas ayudan en esto:

- Reemplazar el tipo con subclases: las subclases se crean para todos los valores de una propiedad particular del objeto. Es simple pero menos flexible ya que no se pueden crear subclases para otras propiedades del objeto.
- Reemplazar el tipo con state/strategy: la clase actual contendrá referencias a los objetos de este tipo y les delegará la ejecución a ellos.

### Pasos para refactorizar

1. Si el condicional está en un método que hace otras cosas, usar el método de extracción
2. Para cada jerarquía de subclase, redefinir el método que contiene el condicional y copiar el código de la rama condicional correspondiente a ese lugar
3. Eliminar esta rama condicional
4. Repetir el reemplazo hasta que el condicional esté vacío. Luego borrarlo y declarar el método como abstracto