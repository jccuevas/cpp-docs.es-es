---
title: Notación de conversión e introducción de safe_cast&lt; &gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- casting
- C-style casts and /clr, motivation for new cast notation
- safe_cast keyword [C++]
ms.assetid: 4eb1d000-3b93-4394-a37b-8b8563f8dc4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 88e8165bde08b65b4f078c4b48863c2088132fca
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427871"
---
# <a name="cast-notation-and-introduction-of-safecastltgt"></a>Notación de conversión e introducción de safe_cast&lt;&gt;

La notación de conversión ha cambiado de extensiones administradas para C++ a Visual C++.

Modificar una estructura existente es una experiencia diferente y más difícil que elaborar la estructura inicial. Hay menos grados de libertad y la solución tiende a es un compromiso entre una reestructuración ideal y lo que es factible dadas las dependencias estructurales existentes.

Extensión de lenguaje es otro ejemplo. En la década de 1990 como la programación orientada a se convirtió en un paradigma importante, la necesidad de una instalación de convertir hacia abajo con seguridad de tipos de C++ se convirtió en presionar. Convertir es la conversión explícita de usuario de un puntero de la clase base o una referencia a un puntero o referencia de una clase derivada. Convertir requiere una conversión explícita. La razón es que el tipo real del puntero de clase base es un aspecto del tiempo de ejecución; el compilador, por tanto, no puede protegerlo. O bien, para volver a formular, una instalación para convertir hacia abajo, al igual que una llamada de función virtual requiere algún tipo de resolución dinámica. Esto provoca dos preguntas:

- ¿Por qué una conversión será necesaria en el paradigma orientado a objetos? ¿No es el mecanismo de función virtual suficiente? Es decir, ¿por qué no se puede reclamar que cualquier necesidad de una conversión (o una conversión de cualquier tipo) es un error de diseño?

- ¿Por qué la compatibilidad de una conversión debe ser un problema en C++? ¿Después de todo, no es un problema en lenguajes orientados a objetos como Smalltalk (o, por consiguiente, Java y C#)? ¿Qué es sobre C++ que hace que sea compatible con una instalación downcast difícil?

Una función virtual representa un algoritmo dependen del tipo común a una familia de tipos. (No estamos considerando interfaces, lo que no se admiten en ISO-C++ pero están disponibles en la programación de CLR y que representan una alternativa de diseño interesantes). El diseño de esa familia normalmente se representa mediante una jerarquía de clases en el que hay una clase base abstracta que declara la interfaz común (las funciones virtuales) y un conjunto de clases derivadas concretas que representan los tipos de familia reales en la aplicación dominio.

Un `Light` jerarquía en un dominio de aplicación equipo genera imágenes (CGI), por ejemplo, tendrán atributos comunes como `color`, `intensity`, `position`, `on`, `off`, y así sucesivamente. Varias de las luces, uno puede controlar mediante la interfaz común sin preocuparse de si una luz en particular es un foco, una luz direccional, una luz no direccional (piense en el sol) o quizá una luz granero puerta. En este caso, no es necesario convertir a un determinado tipo de luz ejercer su interfaz virtual. Sin embargo, en un entorno de producción, velocidad es esencial. Uno podría convertir hacia abajo e invocar explícitamente cada método si al hacerlo, se puede realizar en línea ejecución de las llamadas en lugar de usar el mecanismo virtual.

Por lo tanto, una razón para convertirlo en C++ es para suprimir el mecanismo virtual a cambio de un aumento significativo del rendimiento en tiempo de ejecución. (Tenga en cuenta que la automatización de esta optimización manual es un área activa de investigación. Sin embargo, resulta más difícil resolver que reemplazar el uso explícito de la `register` o `inline` palabra clave.)

Un segundo motivo para convertir hacia abajo deja de ser el doble naturaleza del polimorfismo. Una manera de pensar en polimorfismo se se divide en un par pasivo y dinámico de formularios.

Una invocación virtual (y una función de conversión) representan los usos dinámicos del polimorfismo: uno es realizar una acción según el tipo real del puntero de clase base en esa instancia concreta en la ejecución del programa.

Sin embargo, se asigna un objeto de clase derivada a su puntero de clase base, es una forma pasiva de polimorfismo; el polimorfismo usa como mecanismo de transporte. Este es el uso principal de `Object`, por ejemplo, en la programación de CLR genérico previamente. Cuando se utiliza de forma pasiva, el puntero de clase base elegido para el transporte y almacenamiento normalmente ofrece una interfaz que es demasiado abstracta. `Object`, por ejemplo, proporciona aproximadamente cinco métodos a través de su interfaz; cualquier comportamiento más concreto requiere explícita inferiores. Por ejemplo, si deseamos ajustar el ángulo de nuestras noticias destacadas o su porcentaje de reducción, tendríamos que convertirlo explícitamente. Una interfaz virtual dentro de una familia de subtipos de razones prácticas no puede ser un superconjunto de todos los métodos posibles de sus numerosos elementos secundarios y, por lo que siempre se necesitará una función de conversión dentro de un lenguaje orientado a objetos.

Si una caja fuerte downcast facility es necesaria en un lenguaje orientado a objetos, entonces ¿por qué tarda C++ tanto para agregar uno? El problema radica en cómo hacer disponible la información con respecto al tipo de tiempo de ejecución del puntero. En el caso de una función virtual, la información de tiempo de ejecución se configura en dos partes por el compilador:

- El objeto de clase contiene un miembro de puntero de la tabla virtual adicional (ya sea al principio o al final del objeto de clase; que tiene una historia interesante en sí mismo) que direcciona la tabla virtual adecuada. Por ejemplo, un objeto de contenido destacado de direcciones de una tabla virtual spotlight, una luz direccional, una tabla virtual luz direccional etc.

- Cada función virtual tiene asociada una ranura en la tabla fija y la instancia real para invocar está representada por la dirección almacenada dentro de la tabla. Por ejemplo, virtual `Light` destructor podría estar asociado a la ranura 0, `Color` con la ranura 1 y así sucesivamente. Se trata de una estrategia eficaz si inflexibles porque está configurado en tiempo de compilación y representa una sobrecarga mínima.

El problema, a continuación, es cómo realizar la información de tipo para el puntero sin cambiar el tamaño de los punteros de C++, agregando una segunda dirección o agregando directamente algún tipo de codificación de tipo. Esto no sería aceptable para los programadores (y programas) que decide no utilizar el paradigma orientado a objetos - seguía siendo la Comunidad de usuarios predominante. Otra posibilidad era introducir un puntero especial para tipos de clases polimórficas, pero esto sería confuso y dificultar la mezcla entre los dos, especialmente con problemas de aritmética de puntero. También no sería aceptable para mantener una tabla en tiempo de ejecución que asocia cada puntero al tipo asociado actualmente y actualizarlo dinámicamente.

El problema, a continuación, es un par de comunidades de usuarios que tienen aspiraciones de programación diferentes aunque legítimas. La solución debe ser un compromiso entre las dos comunidades, lo que permite no sólo su aspiración, pero la capacidad de interoperación. Esto significa que las soluciones ofrecidas por cada lado suelen ser factible y la solución se implementa finalmente sea inferior a perfecto. La resolución real gira en torno a la definición de una clase polimórfica: una clase polimórfica es aquel que contiene una función virtual. Una clase polimórfica admite una conversión de seguridad de tipos dinámico. Esto resuelve el problema de mantener-the-puntero-como-address porque todas las clases polimórficas contienen a ese miembro de puntero adicional a su tabla virtual asociada. La información de tipo asociado, por lo tanto, puede almacenarse en una estructura de tabla virtual expandida. El costo de la seguridad de tipos de conversión (casi) se adapta a los usuarios de la instalación.

El siguiente problema con la seguridad de tipos de conversión era su sintaxis. Dado que es una conversión, la propuesta original al Comité de ISO-C++ utilizó la sintaxis de conversión de tipos sencilla, como en este ejemplo:

```
spot = ( SpotLight* ) plight;
```

pero esto ha rechazado el Comité porque no permitió al usuario controlar el costo de la conversión. Si la conversión de seguridad de tipos dinámica tiene la misma sintaxis como la palabra clave unsafe anteriormente pero estática notación de conversión, entonces se convierte en una sustitución y el usuario no tiene capacidad para suprimir la sobrecarga de tiempo de ejecución cuando no es necesaria y quizás demasiado costosas.

En general, en C++, siempre hay un mecanismo por el que se va a suprimir funciones admitidas por el compilador. Por ejemplo, podemos desactivar el mecanismo virtual mediante el operador de ámbito de clase (`Box::rotate(angle)`) o invocando el método virtual a través de un objeto de clase (en lugar de un puntero o referencia de esa clase). Esta última supresión no es necesaria para el idioma, pero es un problema de implementación, similar a la supresión de la construcción de un archivo temporal en una declaración de la forma de calidad:

```
// compilers are free to optimize away the temporary
X x = X::X( 10 );
```

Por lo que la propuesta se dirigirá de nuevo para un nuevo examen, y se tuvieron en cuenta varias notaciones alternativas para la que se volvió al Comité era del formulario (`?type`), que indican indeterminado: es decir, la naturaleza dinámica. Esto daba al usuario la capacidad para alternar entre las dos formas: estáticas o dinámicas - pero nadie estaba muy contento con él. Por lo que resultó de vuelta a dibujar. La notación terceros y correcta es ahora estándar `dynamic_cast<type>`, que se ha generalizado a un conjunto de cuatro notaciones de conversión de nuevo estilo.

En ISO-C++ `dynamic_cast` devuelve `0` cuando se aplica a un tipo de puntero inadecuado y produce una `std::bad_cast` excepción cuando se aplica a un tipo de referencia. En extensiones administradas para C++, aplicar `dynamic_cast` a un tipo de referencia administrada (debido a su representación de puntero) siempre devuelven `0`. `__try_cast<type>` se introdujo como análoga a la variante de inicio de excepciones del `dynamic_cast`, excepto en que produce `System::InvalidCastException` si se produce un error en la conversión.

```
public __gc class ItemVerb;
public __gc class ItemVerbCollection {
public:
   ItemVerb *EnsureVerbArray() [] {
      return __try_cast<ItemVerb *[]>
         (verbList->ToArray(__typeof(ItemVerb *)));
   }
};
```

En la nueva sintaxis, `__try_cast` se ha reasignado como `safe_cast`. Este es el mismo fragmento de código en la nueva sintaxis:

```
public ref class ItemVerb;
public ref class ItemVerbCollection {
public:
   array<ItemVerb^>^ EnsureVerbArray() {
      return safe_cast<array<ItemVerb^>^>
         ( verbList->ToArray( ItemVerb::typeid ));
   }
};
```

En el mundo administrado, es importante permitir código comprobable al limitar la capacidad de los programadores realizar conversiones entre tipos de forma que deje el código no comprobable. Se trata de un aspecto crítico del paradigma de programación dinámico representado por la nueva sintaxis. Por este motivo, las instancias de las conversiones de estilo antiguo se reasignado una de tipo internamente como conversiones de tiempo de ejecución, así que, por ejemplo:

```
// internally recast into the
// equivalent safe_cast expression above
( array<ItemVerb^>^ ) verbList->ToArray( ItemVerb::typeid );
```

Por otro lado, como el polimorfismo proporciona un activo y el modo pasivo, a veces es necesario realizar una conversión para obtener acceso a la API no virtual de un subtipo. Esto puede ocurrir, por ejemplo, con los miembros de una clase que desea dirigirse a cualquier tipo dentro de la jerarquía (polimorfismo pasivo como mecanismo de transporte), pero para el que se conoce la instancia real dentro de un contexto de programa en particular. En este caso, tener una comprobación en tiempo de ejecución de la conversión puede ser una sobrecarga inaceptable. Si es la nueva sintaxis para que actúe como el lenguaje de programación de sistemas administrados, debe proporcionar algún medio de lo que permite un tiempo de compilación (es decir, estáticas) inferiores. Por este motivo la aplicación de la `static_cast` notación puede permanecer un tiempo de compilación de conversión:

```
// ok: cast performed at compile-time.
// No run-time check for type correctness
static_cast< array<ItemVerb^>^>(verbList->ToArray(ItemVerb::typeid));
```

El problema es que no hay ninguna forma de garantizar que el programador que realiza la `static_cast` es correcto y bien intencionado; es decir, no hay ninguna manera de forzar el código administrado que se pueda comprobar. Esto constituye un problema urgente más bajo el paradigma de programación dinámica que nativa, pero no es suficiente dentro de un sistema de lenguaje de programación para no permitir al usuario la capacidad para alternar entre un estático y convertir el tiempo de ejecución.

No hay una trampa de rendimiento y la dificultad en la nueva sintaxis, sin embargo. En la programación nativa, no hay ninguna diferencia en rendimiento entre la notación de conversión de estilo antiguo y el nuevo estilo `static_cast` notación. Pero en la nueva sintaxis, la notación de conversión de estilo antiguo es mucho más cara que el uso del nuevo estilo `static_cast` notación. El motivo es que el compilador transforma internamente el uso de la notación de estilo antiguo en una comprobación en tiempo de ejecución que produce una excepción. Además, también cambia el perfil de ejecución del código porque produce una excepción no detectada hacia abajo de la aplicación: quizás con cuidado, pero el mismo error no iniciaría esta excepción si el `static_cast` se usa la notación. Podría afirmar que esto ayuda a los usuarios en la notación de estilo nuevo. Pero sólo cuando se produce un error; en caso contrario, hará que los programas que usan la notación de estilo antiguo para ralentizar considerablemente sin un conocimiento visible de por qué, similar a las dificultades de los programadores de C siguientes:

```
// pitfall # 1:
// initialization can remove a temporary class object,
// assignment cannot
Matrix m;
m = another_matrix;

// pitfall # 2: declaration of class objects far from their use
Matrix m( 2000, 2000 ), n( 2000, 2000 );
if ( ! mumble ) return;
```

## <a name="see-also"></a>Vea también

[Cambios generales en el lenguaje (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[Conversiones de estilo C con /clr (C++ / c++ / CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)<br/>
[safe_cast](../windows/safe-cast-cpp-component-extensions.md)