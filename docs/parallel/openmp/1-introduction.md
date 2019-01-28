---
title: 1. Introducción
ms.date: 01/16/2019
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
ms.openlocfilehash: 8c735408bdf9f9a13693bd0ad25df185bb1db42a
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087280"
---
# <a name="1-introduction"></a>1. Introducción

Este documento especifica una colección de directivas de compilador, las funciones de biblioteca y las variables de entorno que puede usar para especificar el paralelismo de memoria compartida en los programas C y C++. La funcionalidad descrita en este documento se conoce colectivamente como la *interfaz de programa de aplicaciones (API) de OpenMP C/C ++*. El objetivo de esta especificación es proporcionar un modelo de programación en paralelo que permite que un programa sea portable entre arquitecturas de memoria compartida de diferentes proveedores. Los compiladores de muchos proveedores admiten la API de OpenMP C/C ++. Para obtener más información acerca de OpenMP, incluido el *interfaz de programación de aplicaciones de OpenMP Fortran*, puede encontrarse en el siguiente sitio web:

[https://www.openmp.org](https://www.openmp.org)

Las directivas, las funciones de biblioteca y variables de entorno definidas en este documento le permiten crear y administrar programas paralelos al tiempo que permite la portabilidad. Las directivas de extienden el modelo de programación secuencial C y C++ con el único programa de que estructuras de datos de varios (SPMD), construcciones de uso compartido y construcciones de sincronización. También admiten el uso compartido y privatización en modo de datos. Los compiladores que admiten la de OpenMP C y C++ API incluyen una opción de línea de comandos al compilador que se activa y permite la interpretación de todas las directivas de compilador de OpenMP.

## <a name="11-scope"></a>1.1 Ámbito

Esta especificación describe solo dirigido por el usuario paralelización, en la que definir explícitamente las acciones que el compilador y el sistema de tiempo de ejecución tardan en ejecutar el programa en paralelo. Las implementaciones de OpenMP C y C++ no se requieren para comprobar las dependencias, entra en conflicto, interbloqueos, condiciones de carrera u otros problemas que producen la ejecución del programa incorrecto. Usted es responsable de garantizar que la aplicación con las construcciones OpenMP C y C++ API se ejecuta correctamente. Paralelización automáticas generadas por el compilador y las directivas para el compilador para ayudar a dicha ejecución en paralelo no se tratan en este documento.

## <a name="12-definition-of-terms"></a>1.2 definición de términos

Los siguientes términos se usan en este documento:

- barrier

  Un punto de sincronización que deben alcanzar todos los subprocesos en un equipo.  Cada subproceso esperará hasta que todos los subprocesos en el equipo lleguen en este momento. Existen obstáculos explícitos identificados por las directivas e implícitas barreras creadas por la implementación.

- construct

  Una construcción es una instrucción. Consta de una directiva, seguido de un bloque estructurado. Algunas directivas no forman parte de una construcción. (Consulte *directiva de openmp* en [Apéndice C](c-openmp-c-and-cpp-grammar.md)).

- directiva

  C o C++ `#pragma` seguido por el `omp` identificador, otro texto y una nueva línea. La directiva especifica el comportamiento del programa.

- extensión dinámica

  Todas las instrucciones de la *extensión léxico*, además de cualquier instrucción dentro de una función que se ejecuta como resultado de la ejecución de instrucciones de la extensión léxica. Una extensión dinámica también se conoce como un *región*.

- extensión léxico

  Instrucciones léxicamente conservan en un *bloque estructurado*.

- subproceso principal

  El subproceso que crea un equipo cuando un *región paralela* se ha especificado.

- región paralela

  Instrucciones que enlazar a una construcción paralela de OpenMP y podrán ser ejecutadas por muchos subprocesos.

- private

  Una variable privada nombres de un bloque de almacenamiento que es único para el subproceso que hace la referencia. Hay varias maneras de especificar que una variable privada: una definición dentro de una región paralela, un `threadprivate` directiva, un `private`, `firstprivate`, `lastprivate`, o `reduction` cláusula o el uso de la variable como un `for`bucle variable de control en un `for` inmediatamente después de un bucle un `for` o `parallel for` directiva.

- región

  Una extensión dinámica.

- región de serie

  Las instrucciones ejecutadas únicamente por la *dominar subproceso* fuera de la extensión dinámica de cualquier *región paralela*.

- Serializar

  Para ejecutar una construcción paralela con:

  - un grupo de subprocesos que consta de un único subproceso (que es el subproceso principal para esa construcción paralela),

  - serie orden de ejecución de las instrucciones incluidas en el bloque estructurado (el mismo pedido como si el bloque no formaban parte de una construcción paralela), y

  - ningún efecto en el valor devuelto por `omp_in_parallel()` (aparte de los efectos de cualquier anidados construcciones paralelas).

- shared

  Una variable compartida nombres de un único bloque de almacenamiento. Todos los subprocesos en un equipo que tienen acceso a esta variable también tener acceso a este bloque de almacenamiento único.

- bloque estructurado

  Un bloque estructurado es una instrucción (simple o compuesta) que tiene una sola entrada y una salida única. Si hay un salto dentro o fuera de una instrucción, esa instrucción es un bloque estructurado. (Esta regla incluye una llamada a `longjmp`(3C) o el uso de `throw`, aunque una llamada a `exit` se permite.) Si su ejecución siempre comienza en la apertura `{` y siempre termina en el cierre `}`, una instrucción compuesta es un bloque estructurado. Una instrucción de expresión, la instrucción de selección, la instrucción de iteración, o `try` bloque es un bloque estructurado si obtuvo la correspondiente instrucción compuesta escribiéndolo en `{` y `}` sería un bloque estructurado. Una instrucción de salto, la instrucción con etiqueta o la instrucción de declaración no es un bloque estructurado.

- Equipo

  Uno o varios subprocesos cooperan y cumplen la ejecución de una construcción.

- subproceso

  Una entidad de ejecución tiene un flujo de control serie, un conjunto de variables privadas y el acceso a las variables compartidas.

- variable

  Un identificador, calificado opcionalmente con espacios de nombres, los nombres de un objeto.

## <a name="13-execution-model"></a>1.3 modelo de ejecución

OpenMP usa el modelo de bifurcar-recombinar de ejecución en paralelo. Aunque este modelo bifurcar-recombinar puede ser útil para solucionar diversos problemas, ha sido diseñada para aplicaciones basadas en matrices de gran tamaño. OpenMP está diseñado para admitir programas que se ejecutan correctamente como programas paralelos (biblioteca de compatibilidad de muchos subprocesos de ejecución y un OpenMP completa). También es para los programas que se ejecutan correctamente como secuenciales programas (las directivas que se omiten y una sencilla biblioteca de códigos auxiliares de OpenMP). Sin embargo, es posible y permiten desarrollar un programa que no se comporta correctamente cuando se ejecutan secuencialmente. Además, diferentes grados de paralelismo pueden generar resultados numéricos diferentes debido a cambios en la asociación de las operaciones numéricas. Por ejemplo, una reducción de la adición de serie puede tener un patrón diferente de las asociaciones de adición de una reducción en paralelo. Estas asociaciones diferentes pueden cambiar los resultados de la adición de punto flotante.

Un programa escrito con la API de C/C ++ OpenMP comienza la ejecución como un único subproceso de ejecución llama a la *dominar subproceso*. El subproceso principal se ejecuta en una región de la serie hasta que se encuentra la primera construcción paralela. En la API de C/C ++ OpenMP, el `parallel` Directiva constituye una construcción paralela. Cuando se encuentra una construcción paralela, el subproceso principal crea un grupo de subprocesos y el maestro se convierte en principal del equipo. Cada subproceso en el equipo ejecuta las instrucciones de la extensión dinámica de una región paralela, excepto para las construcciones de uso compartido. Todos los subprocesos en el equipo deben encontrar construcciones de uso compartido en el mismo orden, y uno o varios de los subprocesos ejecutan las instrucciones dentro del bloque estructurado asociado. La barrera implicada al final de una construcción de uso compartido sin una `nowait` cláusula se ejecuta todos los subprocesos en el equipo.

Si un subproceso modifica un objeto compartido, afecta a no solo su propio entorno de ejecución, sino también los de los otros subprocesos del programa. La modificación se garantiza que se complete, desde el punto de vista de otro subproceso, en el siguiente punto de secuencia (como se define en el idioma base) solo si el objeto se declara como volátil. En caso contrario, se garantiza la modificación que se complete después de la modificación de subprocesos en primer lugar. Consulte los otros subprocesos, a continuación, (o al mismo tiempo) un `flush` directiva que especifica el objeto (implícita o explícitamente). Cuando el `flush` directivas que están implícitos en otras directivas de OpenMP no garantizan el orden correcto de efectos secundarios, es responsabilidad del programador para suministrar adicionales, explícita `flush` directivas.

Una vez completada la construcción paralela, para sincronizar los subprocesos en el equipo a una barrera implícita y sólo el subproceso principal continúa la ejecución. Cualquier número de construcciones paralelas se puede especificar en un único programa. Como resultado, un programa puede bifurcar y combinar de muchas veces durante la ejecución.

La API de OpenMP C/C ++ permite a los programadores usar directivas de las funciones ejecutadas desde dentro de construcciones paralelas. Se llama a las directivas que no aparecen en la extensión léxica de una construcción paralela, pero es posible que se encuentran en la extensión dinámica *huérfanos* directivas. Con las directivas de huérfanas, los programadores pueden ejecutar partes importantes de su programa en paralelo, con solo unos cambios mínimos en el programa secuencial. Con esta funcionalidad, puede codificar construcciones paralelas en niveles superiores del árbol de llamadas de sistema y use directivas para controlar la ejecución de cualquiera de las funciones llamadas.

Es posible que las funciones que escriben en el mismo archivo de salida en que los datos escritos por diferentes subprocesos aparecen en orden no determinista de salida de llamadas no sincronizadas para C y C++. De forma similar, no sincronizadas las llamadas a funciones que leen el mismo archivo de entrada pueden leer datos en un orden no determinista. Uso no sincronizada de E/S, que cada subproceso tiene acceso a un archivo diferente, genera los mismos resultados que la ejecución en serie de las funciones de E/S.

## <a name="14-compliance"></a>1.4 Conformidad

Es una implementación de la API de OpenMP C/C ++ *OpenMP conforme* si reconoce y conserva la semántica de todos los elementos de esta especificación, como se definen en los capítulos 1, 2, 3, 4, y son Apéndice C. apéndices A, B, D, E y F para la información solo con fines y no forman parte de la especificación. Las implementaciones que incluyen solo un subconjunto de la API no son compatibles con OpenMP.

El de OpenMP C y C++ API es una extensión para el idioma base que es compatible con una implementación. Si el idioma base no es compatible con una construcción de lenguaje o la extensión que aparece en este documento, la implementación de OpenMP no es necesario para admitirlo.

Todas las funciones de biblioteca estándar de C y C++ y las funciones integradas (es decir, de que el compilador tiene un conocimiento específico de funciones) debe ser seguro para subprocesos. Uso no sincronizada de funciones seguras para subprocesos que diferentes subprocesos dentro de una región paralela no producir un comportamiento indefinido. Sin embargo, el comportamiento puede no ser igual que en una región de la serie. (Una función de generación de números aleatorios es un ejemplo).

La API de C/C ++ OpenMP especifica que es cierto comportamiento *definido por la implementación.* Una implementación de OpenMP conforme se requiere para definir y documentar su comportamiento en estos casos. Para obtener una lista de comportamientos definidos en la implementación, consulte [Apéndice E](e-implementation-defined-behaviors-in-openmp-c-cpp.md).

## <a name="15-normative-references"></a>1.5 referencias de normativa

- ISO/IEC 9899: 1999, *información tecnología - lenguajes de programación - C*. Esta especificación de API de OpenMP se refiere a ISO/IEC 9899: 1999 como C99.

- ¡ISO/IEC 9899: 1990, *información tecnología - lenguajes de programación - C*. Esta especificación de API de OpenMP se refiere a ISO/IEC 9899: 1990 como C90.

- ISO/IEC 14882: 1998, *información tecnología - lenguajes de programación - C++*. Esta especificación de API de OpenMP se refiere a ISO/IEC 14882: 1998 como C++.

Cuando se hace referencia esta especificación de API de OpenMP a C, se hace referencia al idioma base compatible con la implementación.

## <a name="16-organization"></a>1.6 Organización

- [Funciones de biblioteca en tiempo de ejecución](3-run-time-library-functions.md)
- [Variables de entorno](4-environment-variables.md)
- [Definido por la implementación de comportamientos en OpenMP C/C ++](e-implementation-defined-behaviors-in-openmp-c-cpp.md)
- [Nuevas características en OpenMP C/C ++ versión 2.0](f-new-features-and-clarifications-in-version-2-0.md)
