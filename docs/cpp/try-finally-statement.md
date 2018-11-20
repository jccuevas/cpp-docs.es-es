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
ms.openlocfilehash: d05e1d113f4fc661cb6e2e2905fbd8c9dcdd7e2d
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175930"
---
# <a name="try-finally-statement"></a>try-finally (Instrucción)

**Específicos de Microsoft**

La sintaxis siguiente describe el **try-finally** instrucción:

> **\_\_try**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;código protegido<br/>
> }<br/>
> **\_\_Por último**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;código de finalización<br/>
> }<br/>

## <a name="grammar"></a>Gramática

*try-finally-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\_\_Pruebe** *compound-statement*  **\_ \_finalmente** *compound-statement*

El **try-finally** instrucción es una extensión de Microsoft a los lenguajes C y C++ que permite a las aplicaciones de destino garanticen la ejecución del código de limpieza cuando se interrumpe la ejecución de un bloque de código. La limpieza consta de tareas como desasignar memoria, cerrar archivos y liberar identificadores de archivo. El **try-finally** instrucción resulta especialmente útil para las rutinas que tienen varios lugares donde se realiza una comprobación para un error que podría provocar prematura de devolución de la rutina.

Para obtener información relacionada y un ejemplo de código, vea [intente-excepto instrucción](../cpp/try-except-statement.md). Para obtener más información sobre el control general de excepciones estructurado, consulte [Structured Exception Handling](../cpp/structured-exception-handling-c-cpp.md). Para obtener más información sobre cómo controlar las excepciones en aplicaciones administradas, vea [control de excepciones en /clr](../windows/exception-handling-cpp-component-extensions.md).

> [!NOTE]
> El control de excepciones estructurado funciona con Win32 para archivos de código fuente de C y C++. Sin embargo, no está diseñado específicamente para C++. Para asegurarse de que el código será más portable, use el control de excepciones de C++. Además, el control de excepciones de C++ es más flexible, ya que puede controlar excepciones de cualquier tipo. Para los programas de C++, se recomienda utilizar el mecanismo de control de excepciones de C++ ([try, catch y throw](../cpp/try-throw-and-catch-statements-cpp.md) instrucciones).

La instrucción compuesta después de la **__try** cláusula es la sección protegida. La instrucción compuesta después de la **__finally** cláusula es el controlador de terminación. El controlador especifica un conjunto de acciones que se sale de la sección protegida, con independencia de que se salga de la sección protegida a causa de una excepción (finalización anómala) o un paso explícito (finalización normal).

El control alcanza un **__try** instrucción mediante la ejecución secuencial simple (paso explícito). Cuando el control entra en el **__try**, su controlador asociado se vuelve activo. Si el flujo de control alcanza el final del bloque try, la ejecución continúa del modo siguiente:

1. Se invoca al controlador de terminación.

1. Cuando se complete el controlador de terminación, la ejecución continúa después de la **__finally** instrucción. Independientemente de cómo los protegidos de los extremos de la sección (por ejemplo, mediante un **goto** fuera del cuerpo protegido o un **devolver** instrucción), se ejecuta el controlador de terminación *antes* el flujo de control salga de la sección protegida.

   Un **__finally** instrucción no bloquea la búsqueda de un controlador de excepciones adecuado.

Si se produce una excepción en el **__try** bloque, el sistema operativo debe buscar un controlador para la excepción o se producirá un error en el programa. Si se encuentra un controlador, todos los **__finally** se ejecutan bloques y se reanuda la ejecución en el controlador.

Por ejemplo, suponga que una serie de llamadas de función vincula la función A a la función D, como se muestra en la ilustración siguiente. Cada función tiene un controlador de finalización. Si se produce una excepción en la función D y se controla en A, se llama a los controladores de finalización en este orden mientras el sistema desenreda la pila: D, C, B.

![Orden de terminación&#45;ejecución del controlador](../cpp/media/vc38cx1.gif "orden de terminación&#45;ejecución del controlador") <br/>
Orden de terminación-ejecución de controladores

> [!NOTE]
> El comportamiento de try-finally es diferente de otros lenguajes que admiten el uso de **finalmente**, como C#.  Una sola **__try** puede tener, pero no ambos, de **__finally** y **__except**.  Si se van a usar ambos conjuntamente, una instrucción try-except externa debe incluir la instrucción try-finally interna.  Las reglas que especifican cuándo se ejecuta cada bloque también son diferentes.

Para ofrecer compatibilidad con versiones anteriores, **_try**, **_finally**, y **_leave** son sinónimos para **__try**, **__ Por último**, y **__leave** a menos que la opción de compilador [/Za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) se especifica.

## <a name="the-leave-keyword"></a>La palabra clave __leave

El **__leave** palabra clave sólo es válida en la sección protegida de un **try-finally** instrucción y su efecto es saltar al final de la sección protegida. La ejecución continúa en la primera instrucción del controlador de finalización.

Un **goto** instrucción también puede saltar fuera de la sección protegida, pero el rendimiento se degrada porque invoca el desenredo de pila. El **__leave** instrucción es más eficaz porque no produce el desenredo de pila.

## <a name="abnormal-termination"></a>Finalización anómala

Salir de un **try-finally** instrucción mediante el [longjmp](../c-runtime-library/reference/longjmp.md) función en tiempo de ejecución se considera una finalización anómala. No es válido saltar dentro un **__try** instrucción, pero sí fuera. Todos los **__finally** las instrucciones que están activas entre el punto de partida (terminación normal de la **__try** bloque) y el destino (el **__except** que bloquear controla la excepción) se debe ejecutar. Esto recibe el nombre de desenredado local.

Si un **intente** bloque esté terminado prematuramente por cualquier motivo, incluido un salto fuera del bloque, el sistema ejecuta asociado **finalmente** bloque como parte del proceso de desenredo de la pila. En tales casos, el [AbnormalTermination](/windows/desktop/Debug/abnormaltermination) función devuelve **true** si se llama desde dentro el **finalmente** bloquear; en caso contrario, devuelve **false**.

No se llama al controlador de terminación si un proceso se elimina en medio de ejecución de un **try-finally** instrucción.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Escribir un controlador de finalización](../cpp/writing-a-termination-handler.md)<br/>
[Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Sintaxis de controlador de terminación](/windows/desktop/Debug/termination-handler-syntax)