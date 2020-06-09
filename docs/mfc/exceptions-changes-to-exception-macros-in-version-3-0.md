---
title: 'Excepciones: Cambios en las macros de excepción en la versión 3.0'
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: 25095257096efd869e237383c5cd202ae4e602c2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620169"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Excepciones: Cambios en las macros de excepción en la versión 3.0

Este es un tema avanzado.

En la versión 3,0 de MFC y versiones posteriores, las macros de control de excepciones se han cambiado para usar excepciones de C++. En este artículo se indica cómo estos cambios pueden afectar al comportamiento del código existente que usa las macros.

En este artículo se tratan los temas siguientes:

- [Tipos de excepción y la macro CATCH](#_core_exception_types_and_the_catch_macro)

- [Volver a producir excepciones](#_core_re.2d.throwing_exceptions)

## <a name="exception-types-and-the-catch-macro"></a><a name="_core_exception_types_and_the_catch_macro"></a>Tipos de excepción y la macro CATCH

En versiones anteriores de MFC, la macro **catch** usaba información de tipo en tiempo de ejecución de MFC para determinar el tipo de una excepción. el tipo de la excepción se determina, en otras palabras, en el sitio de catch. Sin embargo, con las excepciones de C++, el tipo de la excepción siempre se determina en el sitio de inicio por el tipo del objeto de excepción que se produce. Esto producirá incompatibilidades en el caso excepcional en el que el tipo del puntero al objeto iniciado difiere del tipo del objeto generado.

En el ejemplo siguiente se muestra la consecuencia de esta diferencia entre la versión 3,0 de MFC y las versiones anteriores:

[!code-cpp[NVC_MFCExceptions#1](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

Este código se comporta de forma diferente en la versión 3,0 porque el control siempre pasa al primer bloque **catch** con una declaración de excepción coincidente. Resultado de la expresión Throw

[!code-cpp[NVC_MFCExceptions#19](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

se produce como `CException*` , aunque se construya como `CCustomException` . La macro **catch** de las versiones 2,5 y anteriores de MFC utiliza `CObject::IsKindOf` para probar el tipo en tiempo de ejecución. Dado que la expresión

[!code-cpp[NVC_MFCExceptions#20](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

es true, el primer bloque catch detecta la excepción. En la versión 3,0, que usa excepciones de C++ para implementar muchas de las macros de control de excepciones, el segundo bloque catch coincide con el generado `CException` .

Código como esto es poco habitual. Normalmente aparece cuando un objeto de excepción se pasa a otra función que acepta un genérico `CException*` , realiza el procesamiento "previo a la iniciación" y, por último, produce la excepción.

Para solucionar este problema, mueva la expresión Throw de la función al código de llamada y produzca una excepción del tipo real conocido para el compilador en el momento en que se genera la excepción.

## <a name="re-throwing-exceptions"></a><a name="_core_re.2d.throwing_exceptions"></a>Volver a producir excepciones

Un bloque catch no puede iniciar el mismo puntero de excepción que detectó.

Por ejemplo, este código era válido en versiones anteriores, pero tendrá resultados inesperados con la versión 3,0:

[!code-cpp[NVC_MFCExceptions#2](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

El uso de **Throw** en el bloque catch hace que `e` se elimine el puntero, por lo que el sitio Catch externo recibirá un puntero no válido. Use **THROW_LAST** para volver a iniciar `e` .

Para obtener más información, vea [excepciones: detectar y eliminar excepciones](exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Consulte también

[Control de excepciones](exception-handling-in-mfc.md)
