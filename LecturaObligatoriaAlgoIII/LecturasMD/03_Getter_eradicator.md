## Getter eradicator

Los getters violan el encapsulamiento, pero sigue siendo un poco mejor que hacer los campos públicos. Fowler sugiere no escribir getters hasta que realmente los necesitemos. Además, para Fowler, el punto de encapsular no es ocultar los datos, sino ocultar las decisiones de diseño, particularmente en áreas donde las decisiones pueden cambiar. Es mejor preguntarse "qué pieza que varía estoy ocultando y por qué" en vez de "estoy exponiendo datos". 

El Tell don't Ask se viola cuando tenemos getters, así que deshacernos de ellos puede ayudarnos a mover el comportamiento al lugar correcto. Pero hay muchos casos en los que los objetos necesitan colaborar intercambiando información, lo cual nos hace necesitar los getters. 

Kent Beck dice que siempre hay que tener cuidado con los casos donde el código invoca más de un método del mismo objeto; ¿podemos reemplazarlo con un solo comando?

Otro caso es una Data Class, una clase que solo tiene campos y getters. Casi siempre es un problema porque es falta de comportamiento, hay que sospechar. Fijarse quién usa la información y ver si algo de ese comportamiento puede ser movido al objeto. Acá es útil preguntarse, ¿puedo deshacerme de este getter?

Asignar comportamiento entre objetos es la esencia del diseño orientado a objetos. Colocar el comportamiento en la misma clase que la data es la primer opción. Una buena regla de oro es que las cosas que cambian deben permanecer juntas.

