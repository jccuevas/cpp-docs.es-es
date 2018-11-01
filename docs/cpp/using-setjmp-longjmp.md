---
title: Usar setjmp / longjmp
ms.date: 08/14/2018
f1_keywords:
- longjmp_cpp
- setjmp_cpp
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- setjmpex.h
- longjmp function in C++ programs
- setjmp.h
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
ms.openlocfilehash: 4ead12f79701899b3977993c9de3c3803023150f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525724"
---
# <a name="using-setjmp-and-longjmp"></a>Usar setjmp / longjmp

Cuando [setjmp](../c-runtime-library/reference/setjmp.md) y [longjmp](../c-runtime-library/reference/longjmp.md) son usan juntos, proporcionan una forma de ejecutar un no locales **goto**. Se utilizan normalmente en el código de C para pasar el control de ejecución al código de control de errores o de recuperación en una rutina invocada anteriormente sin usar el estándar de llamada o devolución convenciones.

> [!CAUTION]
> Dado que `setjmp` y `longjmp` no son compatibles con la destrucción correcta de objetos del marco de pila portátil entre los compiladores de C++, y dado que además pueden degradar el rendimiento evitando la optimización en variables locales, no se recomienda su uso en C++ programas. Se recomienda usar **intente** y **catch** construcciones en su lugar.

Si decide usar `setjmp` y `longjmp` en un programa de C++, incluya también \<setjmp.h > o \<setjmpex.h > para garantizar la interacción correcta entre las funciones y excepciones de C++ o de control de excepciones estructurado (SEH) control.

**Específicos de Microsoft**

Si usa un [/EH](../build/reference/eh-exception-handling-model.md) opción para compilar el código de C++, se llaman a destructores para objetos locales durante el desenredo de pila. Sin embargo, si usa **/EHs** o **/EHsc** para compilar y una de las funciones que usa [noexcept](../cpp/noexcept-cpp.md) llamadas `longjmp`, a continuación, el destructor para desenredar para esa función no se puede producir, según el estado del optimizador.

En el código portable, cuando un `longjmp` llamada se ejecuta, destrucción correcta de objetos basado en fotogramas explícitamente no está garantizada por el estándar y no puede admitir otros compiladores. Para que sepa, en el nivel de advertencia 4, una llamada a `setjmp` hace que la advertencia C4611: interacción entre '_setjmp' y la destrucción de objetos de C++ es no portable.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Mezclar excepciones de C (estructuradas) y de C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)
