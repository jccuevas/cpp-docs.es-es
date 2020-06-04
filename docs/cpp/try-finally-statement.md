---
title: try-finally (Instrucción)
ms.date: 11/19/2018
f1_keywords:
- __try
- _try
- __leave_cpp
- __leave
- __finally_cpp
- __try_cpp
- __finally
- _finally
helpviewer_keywords:
- __try keyword [C++]
- __finally keyword [C++]
- __leave keyword [C++]
- try-catch keyword [C++], try-finally keyword
- try-finally keyword [C++]
- __finally keyword [C++], try-finally statement syntax
- __leave keyword [C++], try-finally statement
- structured exception handling [C++], try-finally
ms.assetid: 826e0347-ddfe-4f6e-a7bc-0398e0edc7c2
ms.openlocfilehash: 17f7fb415303ab74f588a2205bc9430127091e96
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825901"
---
# <a name="try-finally-statement"></a>try-finally (Instrucción)

**Específico de Microsoft**

La sintaxis siguiente describe la instrucción **try-finally** :

> **\_\_prueba**<br/>
> {\
> &nbsp;&nbsp;&nbsp;&nbsp;código protegido \
> }\
> **\_\_terminar**\
> {\
> &nbsp;&nbsp;&nbsp;&nbsp;código de terminación \
> }

## <a name="grammar"></a>Gramática

*try-finally-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;try de *la instrucción compuesta* ** \_Finally-Statement \_** ** \_ \_** *compound-statement*

La instrucción **try-finally** es una extensión de Microsoft para los lenguajes C y C++ que permite a las aplicaciones de destino garantizar la ejecución del código de limpieza cuando se interrumpe la ejecución de un bloque de código. La limpieza consta de tareas como desasignar memoria, cerrar archivos y liberar identificadores de archivo. La instrucción **try-finally** es especialmente útil para las rutinas que tienen varios lugares en los que se realiza una comprobación de un error que podría provocar la devolución prematura de la rutina.

Para obtener información relacionada y un ejemplo de código, vea [instrucción try-except](../cpp/try-except-statement.md). Para obtener más información sobre el control de excepciones estructurado en general, vea [control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md). Para obtener más información sobre el control de excepciones en aplicaciones administradas con C++/CLI, vea [control de excepciones en/CLR](../extensions/exception-handling-cpp-component-extensions.md).

> [!NOTE]
> El control de excepciones estructurado funciona con Win32 para archivos de código fuente de C y C++. Sin embargo, no está diseñado específicamente para C++. Para asegurarse de que el código será más portable, use el control de excepciones de C++. Además, el control de excepciones de C++ es más flexible, ya que puede controlar excepciones de cualquier tipo. En el caso de los programas de C++, se recomienda utilizar el mecanismo de control de excepciones de C++ (instrucciones[try, Catch y Throw](../cpp/try-throw-and-catch-statements-cpp.md) ).

La instrucción compuesta después de la cláusula **__try** es la sección protegida. La instrucción compuesta después de la cláusula **__finally** es el controlador de finalización. El controlador especifica un conjunto de acciones que se sale de la sección protegida, con independencia de que se salga de la sección protegida a causa de una excepción (finalización anómala) o un paso explícito (finalización normal).

El control alcanza una **__try** instrucción mediante la ejecución secuencial simple (paso a través). Cuando el control entra en el **__try**, su controlador asociado se activa. Si el flujo de control alcanza el final del bloque try, la ejecución continúa del modo siguiente:

1. Se invoca al controlador de terminación.

1. Cuando el controlador de terminación finaliza, la ejecución continúa después de la instrucción **__finally** . Independientemente de cómo finalice la sección protegida (por ejemplo, a través de un **goto** fuera del cuerpo protegido o una instrucción **Return** ), el controlador de terminación se ejecuta *antes* de que el flujo de control salga de la sección protegida.

   Una instrucción **__finally** no bloquea la búsqueda de un controlador de excepciones adecuado.

Si se produce una excepción en el bloque **__try** , el sistema operativo debe encontrar un controlador para la excepción o se producirá un error en el programa. Si se encuentra un controlador, se ejecutan todos los bloques **__finally** y todos ellos y se reanuda la ejecución en el controlador.

Por ejemplo, suponga que una serie de llamadas de función vincula la función A a la función D, como se muestra en la ilustración siguiente. Cada función tiene un controlador de finalización. Si se produce una excepción en la función D y se controla en A, se llama a los controladores de finalización en este orden mientras el sistema desenreda la pila: D, C, B.

![Orden de terminación&#45;ejecución del controlador](../cpp/media/vc38cx1.gif "Orden de terminación&#45;ejecución del controlador") <br/>
Orden de terminación-ejecución de controladores

> [!NOTE]
> El comportamiento de try-finally es diferente de otros lenguajes que admiten el uso de **Finally**, como C#.  Un único **__try** puede tener, pero no ambos, de **__finally** y **__except**.  Si se van a usar ambos conjuntamente, una instrucción try-except externa debe incluir la instrucción try-finally interna.  Las reglas que especifican cuándo se ejecuta cada bloque también son diferentes.

Por compatibilidad con versiones anteriores, **_try**, **_finally**y **_leave** son sinónimos de **__try**, **__finally**y **__leave** a menos que se especifique la opción del compilador [ \(/za deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="the-__leave-keyword"></a>La palabra clave __leave

La palabra clave **__leave** solo es válida dentro de la sección protegida de una instrucción **try-finally** y su efecto es saltar al final de la sección protegida. La ejecución continúa en la primera instrucción del controlador de finalización.

Una instrucción **goto** también puede saltar fuera de la sección protegida, pero degrada el rendimiento porque invoca el desenredo de la pila. La instrucción **__leave** es más eficaz porque no produce el desenredado de la pila.

## <a name="abnormal-termination"></a>Finalización anómala

Salir de una instrucción **try-finally** mediante la función [longjmp](../c-runtime-library/reference/longjmp.md) en tiempo de ejecución se considera una finalización anómala. No es válido saltar a una instrucción **__try** , pero es legal salir de una. Se deben ejecutar todas las instrucciones **__finally** que estén activas entre el punto de salida (terminación normal del bloque de **__try** ) y el destino (el bloque **__except** que controla la excepción). Esto recibe el nombre de desenredado local.

Si un bloque **try** se termina prematuramente por cualquier motivo, incluido un salto fuera del bloque, el sistema ejecuta el bloque **Finally** asociado como parte del proceso de desenredado de la pila. En tales casos, la función [AbnormalTermination](/windows/win32/Debug/abnormaltermination) devuelve **true** si se llama desde dentro del bloque **Finally** ; de lo contrario, devuelve **false**.

No se llama al controlador de terminación si un proceso se elimina en medio de la ejecución de una instrucción **try-finally** .

**FINALIZAR específico de Microsoft**

## <a name="see-also"></a>Consulte también

[Escribir un controlador de finalización](../cpp/writing-a-termination-handler.md)<br/>
[Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Sintaxis del controlador de terminación](/windows/win32/Debug/termination-handler-syntax)
