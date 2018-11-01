---
title: Recomendaciones de optimización
ms.date: 11/04/2016
helpviewer_keywords:
- Visual C++, optimization
- optimization, best practices
ms.assetid: f3433148-7255-4ca6-8a4f-7c31aac88508
ms.openlocfilehash: 67a071ecd457495510b2015f05466e1aa9bfc989
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477355"
---
# <a name="optimization-best-practices"></a>Recomendaciones de optimización

En este documento se describen algunos procedimientos recomendados para la optimización en Visual C++.

## <a name="compiler-and-linker-options"></a>Opciones del compilador y del vinculador

### <a name="profile-guided-optimization"></a>Optimización guiada por perfiles

Visual C++ admite *optimización guiada por perfiles* (PGO). Esta optimización utiliza datos de perfil de ejecuciones de entrenamiento de una versión instrumentada de una aplicación para controlar la optimización posterior de la aplicación. La utilización de PGO puede ocupar mucho tiempo; por tanto, no lo deberían utilizar todos los desarrolladores, sino que se recomienda utilizar PGO para la versión de lanzamiento final de un producto. Para obtener más información, consulte [optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md).

Además, *Whole Program Optimization* (también se conoce como generación de código de tiempo de vínculo) y la **/O1** y **/O2** se han mejorado las optimizaciones. En general, una aplicación compilada con una de estas opciones es más rápida que la misma aplicación compilada con un compilador anterior.

Para obtener más información, consulte [/GL (Whole Program Optimization)](../../build/reference/gl-whole-program-optimization.md) y [/O1, / O2 (minimizar tamaño, maximizar velocidad)](../../build/reference/o1-o2-minimize-size-maximize-speed.md).

### <a name="which-level-of-optimization-to-use"></a>Qué nivel de optimización para usar

Si es posible, las últimas versiones de lanzamiento se deberían compilar con las optimizaciones guiadas por perfiles. Si no es posible generar con PGO, ya sea debido a una infraestructura insuficiente para ejecutar las compilaciones instrumentadas, o bien por no tener acceso a los escenarios, se recomienda realizar la generación con la optimización de todo el programa.

El **/Gy** conmutador es también muy útil. Genera un COMDAT independiente para cada función, dando más flexibilidad al vinculador cuando quita COMDAT sin referencia y plegamiento de COMDAT. La única desventaja de utilizar **/Gy** es que puede causar problemas al depurar. Por consiguiente, por lo general se recomienda utilizarlo. Para obtener más información, consulte [/Gy (Habilitar vinculación en el nivel de función)](../../build/reference/gy-enable-function-level-linking.md).

Para vincular en entornos de 64 bits, se recomienda usar la **/OPT: REF, ICF** opción del vinculador y en entornos de 32 bits, **/OPT: ref** se recomienda. Para obtener más información, consulte [/OPT (optimizaciones)](../../build/reference/opt-optimizations.md).

También se recomienda encarecidamente generar símbolos de depuración, incluso con versiones de lanzamiento optimizadas. No afecta al código generado y facilita la depuración de la aplicación, si fuera necesario.

### <a name="floating-point-switches"></a>Modificadores de punto flotante

El **/op.** ha quitado la opción del compilador, y se han agregado las siguientes cuatro opciones del compilador tratar con optimizaciones de punto flotante:

|||
|-|-|
|**/ fp: precisa**|Ésta es la recomendación predeterminada y se debería utilizar en la mayoría de los casos.|
|**/ fp: Fast**|Se recomienda si el rendimiento es de la máxima importancia; por ejemplo, en juegos. Dará como resultado un rendimiento mucho más rápido.|
|**/ fp: strict**|Se recomienda si necesitan excepciones en punto flotante y si se desea el comportamiento IEEE. Dará como resultado el rendimiento más lento.|
|**/ fp: except [-]**|Se puede usar junto con **/fp: strict** o **/fp: precisa**, pero no **/fp: Fast**.|

Para obtener más información, consulte [/fp (Especificar comportamiento de punto flotante)](../../build/reference/fp-specify-floating-point-behavior.md).

## <a name="optimization-declspecs"></a>Modificadores declspec de optimización

En esta sección, se examinarán dos modificadores declspec que se pueden utilizar en programas para mejorar el rendimiento: `__declspec(restrict)` y `__declspec(noalias)`.

El modificador declspec `restrict` sólo se puede aplicar a declaraciones de función que devuelven un puntero, como `__declspec(restrict) void *malloc(size_t size);`

El modificador declspec `restrict` se utiliza en funciones que devuelven punteros sin alias. Esta palabra clave se utiliza para la implementación de la biblioteca en tiempo de ejecución de C de `malloc` ya que nunca devolverá un valor de puntero que se esté utilizando en el programa actual (salvo que se esté haciendo algo no válido, como utilizar la memoria después de liberarla).

El modificador declspec `restrict` da más información al compilador para realizar las optimizaciones del compilador. Una de las tareas que más le cuesta al compilador es determinar qué punteros son alias de otros punteros y esta información ayuda considerablemente al compilador.

Merece la pena indicar que es una sugerencia para el compilador, no algo que el compilador vaya a comprobar. Si el programa utiliza el modificador declspec `restrict` de manera inapropiada, el programa podrá tener un comportamiento incorrecto.

Para obtener más información, consulte [restringir](../../cpp/restrict.md).

El modificador declspec `noalias` también se aplica sólo a funciones, e indica que la función es una función semipura. Una función semipura es aquella que modifica o hace referencia únicamente a variables locales, argumentos y direccionamientos indirectos de primer nivel de argumentos. Este modificador declspec es una sugerencia para el compilador, y si la función hace referencia a variables globales o direccionamientos indirectos de segundo nivel de argumentos a punteros, el compilador podrá generar código que interrumpa la aplicación.

Para obtener más información, consulte [noalias](../../cpp/noalias.md).

## <a name="optimization-pragmas"></a>Directivas pragma de optimización

Hay también varias directivas pragma útiles para ayudar a optimizar el código. La primera que se describirá es `#pragma optimize`:

```cpp
#pragma optimize("{opt-list}", on | off)
```

Esta directiva pragma le permite establecer un nivel de optimización función a función. Este sistema es perfecto para esas raras ocasiones en las que la aplicación se bloquea cuando una función determinada se compila con optimización. Puede utilizarlo para desactivar las optimizaciones para una función única:

```cpp
#pragma optimize("", off)
int myFunc() {...}
#pragma optimize("", on)
```

Para obtener más información, consulte [optimizar](../../preprocessor/optimize.md).

Los procesos en línea son una de las optimizaciones más importantes que ejecuta el compilador y aquí se van a describir un par de directivas pragma que ayudan a modificar este comportamiento.

`#pragma inline_recursion` es útil para especificar si se desea o no que la aplicación procese en línea una llamada recursiva. De forma predeterminada está desactivada. En el caso de recursividad superficial de funciones pequeñas, puede activarla. Para obtener más información, consulte [inline_recursion](../../preprocessor/inline-recursion.md).

Otra directiva pragma útil para limitar la profundidad del procesamiento en línea es `#pragma inline_depth`. Sobre todo resulta útil en aquellas situaciones en las que se intenta limitar el tamaño de un programa o función. Para obtener más información, consulte [inline_depth](../../preprocessor/inline-depth.md).

## <a name="restrict-and-assume"></a>__restrict y \__assume

Hay un par de palabras clave en Visual C++ que pueden mejorar el rendimiento: [__restrict](../../cpp/extension-restrict.md) y [__assume](../../intrinsics/assume.md).

En primer lugar, se debería tener en cuenta que `__restrict` y `__declspec(restrict)` son diferentes. Aunque están relacionadas de algún modo, su semántica es diferente. `__restrict` es un calificador de tipo, como `const` o `volatile`, pero exclusivamente para los tipos de puntero.

Un puntero que se modifica con `__restrict` se conoce como un *puntero __restrict*. Un puntero __restrict es un puntero que solo se puede acceder a través de la \__restrict puntero. En otras palabras, no se puede usar otro puntero para tener acceso a los datos que apunta el \__restrict puntero.

`__restrict` puede ser una herramienta eficaz para el optimizador de Visual C++, pero hay que utilizarla con cuidado. Si se utiliza incorrectamente, el optimizador podría realizar una optimización que interrumpiría su aplicación.

El `__restrict` reemplaza la palabra clave el **/OA** cambiar desde versiones anteriores.

Con `__assume`, un desarrollador puede indicar al compilador realizar suposiciones sobre el valor de alguna variable.

Por ejemplo, `__assume(a < 5);` indica al optimizador que en esa línea de código la variable `a` es menor que 5. De nuevo, esto es una sugerencia para el compilador. Si `a` es realmente 6 es en este punto del programa, el comportamiento de este después de que el compilador haya realizado la optimización puede ser distinto de lo que se esperaba. `__assume` es más útil antes de cambiar instrucciones o expresiones condicionales.

Hay algunas limitaciones en `__assume`. En primer lugar, al igual que `__restrict`, es sólo una sugerencia, por lo que el compilador puede omitirlo sin mayor problema. Además, `__assume` funciona actualmente sólo con desigualdades de variables frente a constantes. No difunde desigualdades simbólicas, por ejemplo, assume(a < b).

## <a name="intrinsic-support"></a>Compatibilidad intrínseca

Las funciones intrínsecas son llamadas a función en las que el compilador tiene un conocimiento intrínseco sobre la llamada, y en lugar de llamar a una función de una biblioteca, emite código para esa función. El archivo de encabezado \<intrin.h > contiene todas las funciones intrínsecas disponibles para cada una de las plataformas de hardware compatible.

Las funciones intrínsecas dan al programador la capacidad para profundizar en el código sin tener que utilizar el ensamblado. Las funciones intrínsecas presentan varias ventajas:

- El código es más portátil. Algunas de las funciones intrínsecas están disponibles en varias arquitecturas de la CPU.

- El código es más fácil de leer, ya que se sigue escribiendo en C/C++.

- El código presenta las ventajas de las optimizaciones del compilador. A medida que el compilador mejora, también lo hace la generación de código para las funciones intrínsecas.

Para obtener más información, consulte [intrínsecos del compilador](../../intrinsics/compiler-intrinsics.md).

## <a name="exceptions"></a>Excepciones

Hay una merma en el rendimiento asociada al uso de excepciones. Se introducen algunas restricciones al utilizar bloques Try que impiden que el compilador realice ciertas optimizaciones. En las plataformas x86 hay una degradación del rendimiento adicional de los bloques Try debido a la información de estado adicional que se debe generar durante la ejecución del código. En las plataformas de 64 bits, los bloques Try no degradan tanto el rendimiento, pero cuando se produce la excepción, el proceso de encontrar el controlador y desenredar la pila puede ser costoso.

Por consiguiente, se recomienda evitar la introducción de bloques Try/Catch en código que no lo necesite realmente. Si tiene que usar excepciones, utilice si es posible excepciones sincrónicas. Para obtener más información, vea [Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md).

Por último, sólo produzca excepciones para casos excepcionales. La utilización de excepciones para el flujo de control general probablemente hagan que el rendimiento se resienta.

## <a name="see-also"></a>Vea también

- [Optimizar el código](../../build/reference/optimizing-your-code.md)
