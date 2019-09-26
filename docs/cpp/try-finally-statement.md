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
ms.openlocfilehash: c26b72f7c675a4130f38c515cf71ecc290328ccc
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "69498608"
---
# <a name="try-finally-statement"></a>try-finally (Instrucción)

**Específicos de Microsoft**

La sintaxis siguiente describe la instrucción **try-finally** :

> **\_\_prueba**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;código protegido<br/>
> }<br/>
> **\_\_terminar**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;código de terminación<br/>
> }

## <a name="grammar"></a>Gramática

*try-finally-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;try de *la instrucción compuesta*  **Finally-Statement\_ \_**  **\_ \_**

La instrucción **try-finally** es una extensión de Microsoft para los C++ lenguajes C y que permite a las aplicaciones de destino garantizar la ejecución del código de limpieza cuando se interrumpe la ejecución de un bloque de código. La limpieza consta de tareas como desasignar memoria, cerrar archivos y liberar identificadores de archivo. La instrucción **try-finally** es especialmente útil para las rutinas que tienen varios lugares en los que se realiza una comprobación de un error que podría provocar la devolución prematura de la rutina.

Para obtener información relacionada y un ejemplo de código, vea [instrucción try-except](../cpp/try-except-statement.md). Para obtener más información sobre el control de excepciones estructurado en general, vea [control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md). Para obtener más información sobre cómo controlar las excepciones en C++las aplicaciones administradas con/CLI, vea [control de excepciones en/CLR](../extensions/exception-handling-cpp-component-extensions.md).

> [!NOTE]
> El control de excepciones estructurado funciona con Win32 para archivos de código fuente de C y C++. Sin embargo, no está diseñado específicamente para C++. Para asegurarse de que el código será más portable, use el control de excepciones de C++. Además, el control de excepciones de C++ es más flexible, ya que puede controlar excepciones de cualquier tipo. En C++ el caso de los programas, se recomienda usar C++ el mecanismo de control de excepciones (instrucciones[try, Catch y Throw](../cpp/try-throw-and-catch-statements-cpp.md) ).

La instrucción compuesta después de la cláusula **_ _ try** es la sección protegida. La instrucción compuesta después de la cláusula **_ _ Finally** es el controlador de finalización. El controlador especifica un conjunto de acciones que se sale de la sección protegida, con independencia de que se salga de la sección protegida a causa de una excepción (finalización anómala) o un paso explícito (finalización normal).

El control alcanza una instrucción **_ _ try** mediante una ejecución secuencial simple (paso a través). Cuando el control entra en el **_ _ try**, su controlador asociado se activa. Si el flujo de control alcanza el final del bloque try, la ejecución continúa del modo siguiente:

1. Se invoca al controlador de terminación.

1. Cuando el controlador de terminación finaliza, la ejecución continúa después de la instrucción **_ _ Finally** . Independientemente de cómo finalice la sección protegida (por ejemplo, a través de un **goto** fuera del cuerpo protegido o una instrucción **Return** ), el controlador de terminación se ejecuta *antes* de que el flujo de control salga de la sección protegida.

   Una instrucción **_ _ Finally** no bloquea la búsqueda de un controlador de excepciones adecuado.

Si se produce una excepción en el bloque **_ _ try** , el sistema operativo debe encontrar un controlador para la excepción o se producirá un error en el programa. Si se encuentra un controlador, se ejecutan todos los bloques **_ _ Finally** y se reanuda la ejecución en el controlador.

Por ejemplo, suponga que una serie de llamadas de función vincula la función A a la función D, como se muestra en la ilustración siguiente. Cada función tiene un controlador de finalización. Si se produce una excepción en la función D y se controla en, se llama a los controladores de finalización en este orden cuando el sistema desenreda la pila: D, C, B.

![Orden de ejecución&#45;del controlador](../cpp/media/vc38cx1.gif "de terminación orden&#45;de ejecución del controlador de finalización") <br/>
Orden de terminación-ejecución de controladores

> [!NOTE]
> El comportamiento de try-finally es diferente de otros lenguajes que admiten el uso de **Finally**, como C#.  Un único **_ _ try** puede tener, pero no ambos, de **_ _ Finally** y **_ _ Except**.  Si se van a usar ambos conjuntamente, una instrucción try-except externa debe incluir la instrucción try-finally interna.  Las reglas que especifican cuándo se ejecuta cada bloque también son diferentes.

Por compatibilidad con versiones anteriores, **_try**, **_finally**y **_leave** son sinónimos para **_ _ try**, **_ _ Finally**y **__leave** a menos que la opción del compilador [/za \(deshabilite extensiones de lenguaje. ](../build/reference/za-ze-disable-language-extensions.md)se especifica.

## <a name="the-__leave-keyword"></a>La palabra clave __leave

La palabra clave **__leave** solo es válida dentro de la sección protegida de una instrucción **try-finally** y su efecto es saltar al final de la sección protegida. La ejecución continúa en la primera instrucción del controlador de finalización.

Una instrucción **goto** también puede saltar fuera de la sección protegida, pero degrada el rendimiento porque invoca el desenredo de la pila. La instrucción **__leave** es más eficaz porque no produce el desenredado de la pila.

## <a name="abnormal-termination"></a>Finalización anómala

Salir de una instrucción **try-finally** mediante la función [longjmp](../c-runtime-library/reference/longjmp.md) en tiempo de ejecución se considera una finalización anómala. No es válido saltar a una instrucción **_ _ try** , pero es legal salir de una. Se deben ejecutar todas las instrucciones **_ _ Finally** activas entre el punto de salida (terminación normal del bloque **_ _ try** ) y el destino (el bloque **_ _ Except** que controla la excepción). Esto recibe el nombre de desenredado local.

Si un bloque **try** se termina prematuramente por cualquier motivo, incluido un salto fuera del bloque, el sistema ejecuta el bloque **Finally** asociado como parte del proceso de desenredado de la pila. En tales casos, la función [AbnormalTermination](/windows/win32/Debug/abnormaltermination) devuelve **true** si se llama desde dentro del bloque **Finally** ; de lo contrario, devuelve **false**.

No se llama al controlador de terminación si un proceso se elimina en medio de la ejecución de una instrucción **try-finally** .

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Escribir un controlador de finalización](../cpp/writing-a-termination-handler.md)<br/>
[Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Sintaxis del controlador de terminación](/windows/win32/Debug/termination-handler-syntax)