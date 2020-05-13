---
title: Procedimientos recomendados para la optimización
ms.date: 05/06/2019
helpviewer_keywords:
- C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: 541114b4cbf7d3d063e48b50ab265b4c95c6237c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328451"
---
# <a name="optimization-best-practices"></a>Procedimientos recomendados para la optimización

En este documento se describen algunas prácticas recomendadas para optimizar los programas C++ en Visual Studio.

## <a name="compiler-and-linker-options"></a>Opciones del compilador y del vinculador

### <a name="profile-guided-optimization"></a>Optimización guiada por perfiles

Visual Studio admite la *optimización guiada por perfiles* (PGO). Esta optimización utiliza datos de perfil de ejecuciones de entrenamiento de una versión instrumentada de una aplicación para impulsar la optimización posterior de la aplicación. La utilización de PGO puede ocupar mucho tiempo; por tanto, no lo deberían utilizar todos los desarrolladores, sino que se recomienda utilizar PGO para la versión de lanzamiento final de un producto. Para más información, vea [Optimizaciones guiadas por perfiles](profile-guided-optimizations.md).

Además, se ha mejorado la *optimización* de todo el programa (también conocido como generación de código de tiempo de enlace) y las optimizaciones **/O1** y **/O2.** En general, una aplicación compilada con una de estas opciones es más rápida que la misma aplicación compilada con un compilador anterior.

Para obtener más información, vea [/GL (Optimización](reference/gl-whole-program-optimization.md) de todo el programa) y [/O1, /O2 (Minimizar tamaño, Maximizar velocidad)](reference/o1-o2-minimize-size-maximize-speed.md).

### <a name="which-level-of-optimization-to-use"></a>Qué nivel de optimización utilizar

Si es posible, las últimas versiones de lanzamiento se deberían compilar con las optimizaciones guiadas por perfiles. Si no es posible generar con PGO, ya sea debido a una infraestructura insuficiente para ejecutar las compilaciones instrumentadas, o bien por no tener acceso a los escenarios, se recomienda realizar la generación con la optimización de todo el programa.

El modificador **/Gy** también es muy útil. Genera un COMDAT independiente para cada función, dando más flexibilidad al vinculador cuando quita COMDAT sin referencia y plegamiento de COMDAT. La única desventaja de usar **/Gy** es que puede causar problemas al depurar. Por consiguiente, por lo general se recomienda utilizarlo. Para obtener más información, consulte [/Gy (Habilitar vinculación en el nivel de función)](reference/gy-enable-function-level-linking.md).

Para la vinculación en entornos de 64 bits, se recomienda utilizar la opción del vinculador **/OPT:REF,ICF** y, en entornos de 32 bits, se recomienda **/OPT:REF.** Para obtener más información, vea [/OPT (Optimizaciones)](reference/opt-optimizations.md).

También se recomienda encarecidamente generar símbolos de depuración, incluso con versiones de lanzamiento optimizadas. No afecta al código generado y hace que sea mucho más fácil depurar la aplicación, si es necesario.

### <a name="floating-point-switches"></a>Interruptores de punto flotante

Se ha quitado la opción del compilador **/Op** y se han agregado las cuatro opciones del compilador siguientes que tratan con optimizaciones de punto flotante:

|||
|-|-|
|**/fp:precise**|Ésta es la recomendación predeterminada y se debería utilizar en la mayoría de los casos.|
|**/fp:rápido**|Se recomienda si el rendimiento es de la máxima importancia; por ejemplo, en juegos. Dará como resultado un rendimiento mucho más rápido.|
|**/fp:estricto**|Se recomienda si necesitan excepciones en punto flotante y si se desea el comportamiento IEEE. Dará como resultado el rendimiento más lento.|
|**/fp:except[-]**|Se puede utilizar junto con **/fp:strict** o **/fp:precise**, pero no **/fp:fast**.|

Para obtener más información, consulte [/fp (Especificar comportamiento de punto flotante)](reference/fp-specify-floating-point-behavior.md).

## <a name="optimization-declspecs"></a>Declspecs de optimización

En esta sección, se examinarán dos modificadores declspec que se pueden utilizar en programas para mejorar el rendimiento: `__declspec(restrict)` y `__declspec(noalias)`.

El modificador declspec `restrict` sólo se puede aplicar a declaraciones de función que devuelven un puntero, como `__declspec(restrict) void *malloc(size_t size);`

El modificador declspec `restrict` se utiliza en funciones que devuelven punteros sin alias. Esta palabra clave se utiliza para la implementación de la biblioteca en tiempo de ejecución de C de `malloc` ya que nunca devolverá un valor de puntero que se esté utilizando en el programa actual (salvo que se esté haciendo algo no válido, como utilizar la memoria después de liberarla).

El modificador declspec `restrict` da más información al compilador para realizar las optimizaciones del compilador. Una de las tareas que más le cuesta al compilador es determinar qué punteros son alias de otros punteros y esta información ayuda considerablemente al compilador.

Merece la pena indicar que es una sugerencia para el compilador, no algo que el compilador vaya a comprobar. Si el programa utiliza el modificador declspec `restrict` de manera inapropiada, el programa podrá tener un comportamiento incorrecto.

Para obtener más información, consulte [restringir](../cpp/restrict.md).

El modificador declspec `noalias` también se aplica sólo a funciones, e indica que la función es una función semipura. Una función semipura es aquella que modifica o hace referencia únicamente a variables locales, argumentos y direccionamientos indirectos de primer nivel de argumentos. Este modificador declspec es una sugerencia para el compilador, y si la función hace referencia a variables globales o direccionamientos indirectos de segundo nivel de argumentos a punteros, el compilador podrá generar código que interrumpa la aplicación.

Para obtener más información, consulte [noalias](../cpp/noalias.md).

## <a name="optimization-pragmas"></a>Pragmas de optimización

Hay también varias directivas pragma útiles para ayudar a optimizar el código. El primero que discutiremos `#pragma optimize`es:

```cpp
#pragma optimize("{opt-list}", on | off)
```

Esta directiva pragma le permite establecer un nivel de optimización función a función. Este sistema es perfecto para esas raras ocasiones en las que la aplicación se bloquea cuando una función determinada se compila con optimización. Puede utilizarlo para desactivar las optimizaciones para una función única:

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

Para obtener más información, consulte [Optimizar](../preprocessor/optimize.md)archivos .

Los procesos en línea son una de las optimizaciones más importantes que ejecuta el compilador y aquí se van a describir un par de directivas pragma que ayudan a modificar este comportamiento.

`#pragma inline_recursion` es útil para especificar si se desea o no que la aplicación procese en línea una llamada recursiva. De forma predeterminada está desactivada. En el caso de recursividad superficial de funciones pequeñas, puede activarla. Para obtener más información, consulte [inline_recursion](../preprocessor/inline-recursion.md).

Otra directiva pragma útil para limitar la profundidad del procesamiento en línea es `#pragma inline_depth`. Esto suele ser útil en situaciones en las que intenta limitar el tamaño de un programa o función. Para obtener más información, consulte [inline_depth](../preprocessor/inline-depth.md).

## <a name="__restrict-and-__assume"></a>__restrict \_y _assume

Hay un par de palabras clave en Visual Studio que pueden ayudar al rendimiento: [__restrict](../cpp/extension-restrict.md) y [__assume](../intrinsics/assume.md).

En primer lugar, se debería tener en cuenta que `__restrict` y `__declspec(restrict)` son diferentes. Aunque están relacionadas de algún modo, su semántica es diferente. `__restrict` es un calificador de tipo, como `const` o `volatile`, pero exclusivamente para los tipos de puntero.

Un puntero que `__restrict` se modifica con se conoce como puntero *__restrict*. Un puntero __restrict es un puntero al \_que solo se puede tener acceso a través del puntero _restrict. En otras palabras, no se puede utilizar otro \_puntero para tener acceso a los datos señalados por el puntero _restrict.

`__restrict`puede ser una herramienta poderosa para el optimizador de Microsoft C++, pero úselo con mucho cuidado. Si se utiliza incorrectamente, el optimizador podría realizar una optimización que interrumpiría su aplicación.

La `__restrict` palabra clave reemplaza el modificador **/Oa** de versiones anteriores.

Con `__assume`, un desarrollador puede indicar al compilador que haga suposiciones sobre el valor de alguna variable.

Por ejemplo, `__assume(a < 5);` indica al optimizador que en esa línea de código la variable `a` es menor que 5. De nuevo, esto es una sugerencia para el compilador. Si `a` es realmente 6 es en este punto del programa, el comportamiento de este después de que el compilador haya realizado la optimización puede ser distinto de lo que se esperaba. `__assume` es más útil antes de cambiar instrucciones o expresiones condicionales.

Hay algunas limitaciones en `__assume`. En primer lugar, al igual que `__restrict`, es sólo una sugerencia, por lo que el compilador puede omitirlo sin mayor problema. Además, `__assume` funciona actualmente sólo con desigualdades de variables frente a constantes. No propaga desigualdades simbólicas, por ejemplo, asume (un < b).

## <a name="intrinsic-support"></a>Soporte intrínseco

Las funciones intrínsecas son llamadas a función en las que el compilador tiene un conocimiento intrínseco sobre la llamada, y en lugar de llamar a una función de una biblioteca, emite código para esa función. El archivo \<de encabezado intrin.h> contiene todos los elementos intrínsecos disponibles para cada una de las plataformas de hardware compatibles.

Las funciones intrínsecas dan al programador la capacidad para profundizar en el código sin tener que utilizar el ensamblado. Las funciones intrínsecas presentan varias ventajas:

- El código es más portátil. Algunas de las funciones intrínsecas están disponibles en varias arquitecturas de la CPU.

- El código es más fácil de leer, ya que se sigue escribiendo en C/C++.

- El código presenta las ventajas de las optimizaciones del compilador. A medida que el compilador mejora, también lo hace la generación de código para las funciones intrínsecas.

Para obtener más información, consulte [Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md).

## <a name="exceptions"></a>Excepciones

Hay una merma en el rendimiento asociada al uso de excepciones. Se introducen algunas restricciones al utilizar bloques Try que impiden que el compilador realice ciertas optimizaciones. En las plataformas x86 hay una degradación del rendimiento adicional de los bloques Try debido a la información de estado adicional que se debe generar durante la ejecución del código. En las plataformas de 64 bits, los bloques Try no degradan tanto el rendimiento, pero cuando se produce la excepción, el proceso de encontrar el controlador y desenredar la pila puede ser costoso.

Por consiguiente, se recomienda evitar la introducción de bloques Try/Catch en código que no lo necesite realmente. Si tiene que usar excepciones, utilice si es posible excepciones sincrónicas. Para obtener más información, vea [Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md).

Por último, sólo produzca excepciones para casos excepcionales. La utilización de excepciones para el flujo de control general probablemente hagan que el rendimiento se resienta.

## <a name="see-also"></a>Consulte también

- [Optimizar el código](optimizing-your-code.md)
