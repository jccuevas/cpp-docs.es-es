---
title: 'Excepciones: Cambios en las Macros de excepción en la versión 3.0 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8829c018e51b81c0997092312e3e058d3086665b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417038"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Excepciones: Cambios en las macros de excepción en la versión 3.0

Se trata de un tema avanzado.

En la versión 3.0 y versiones posterior de MFC, las macros de control de excepciones se cambiaron para usar las excepciones de C++. Este artículo explica cómo estos cambios pueden afectar al comportamiento del código existente que utiliza las macros.

En este artículo se tratan los siguientes temas:

- [Tipos de excepción y la macro CATCH](#_core_exception_types_and_the_catch_macro)

- [Volver a generar excepciones](#_core_re.2d.throwing_exceptions)

##  <a name="_core_exception_types_and_the_catch_macro"></a> Tipos de excepción y la Macro CATCH

En versiones anteriores de MFC, la **CATCH** macro usa información de tipo en tiempo de ejecución MFC para determinar el tipo de la excepción; se determina el tipo de excepción, en otras palabras, en el bloque catch. Con las excepciones de C++, sin embargo, el tipo de excepción siempre viene determinada en el sitio de producción por el tipo del objeto de excepción que se produce. Esto hará que las incompatibilidades en el caso excepcional donde el tipo de puntero al objeto iniciado difiere el tipo del objeto iniciado.

El ejemplo siguiente muestra el resultado de esta diferencia entre la versión 3.0 de MFC y las versiones anteriores:

[!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

Este código se comporta de forma diferente en la versión 3.0 porque el control siempre se pasa a la primera **catch** bloque con una declaración de excepción coincidente. El resultado de la expresión throw

[!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

se produce como un `CException*`, aunque se construye como un `CCustomException`. El **CATCH** macro en las versiones de MFC 2.5 y versiones anteriores utilizan `CObject::IsKindOf` para probar el tipo en tiempo de ejecución. Dado que la expresión

[!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

es true, el primer bloque catch detecta la excepción. En la versión 3.0, que usa las excepciones de C++ para implementar muchas de las macros de control de excepciones, el segundo bloque catch coincide con la producida `CException`.

Es raro que código similar al siguiente. Suele aparecer cuando un objeto de excepción se pasa a otra función que acepta un tipo genérico `CException*`, realiza el procesamiento de "previo a throw" y, por último, se produce la excepción.

Para solucionar este problema, mueva la expresión throw desde la función al código de llamada e inicia una excepción del tipo real conocida por el compilador en el momento en que se genera la excepción.

##  <a name="_core_re.2d.throwing_exceptions"></a> Volver a generar excepciones

Un bloque catch no puede producir el mismo puntero de la excepción que detectó.

Por ejemplo, este código fue válido en las versiones anteriores, pero tendrá resultados inesperados con la versión 3.0:

[!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

Mediante **THROW** hace que el puntero en la instrucción catch bloque `e` eliminarse para que el bloque catch externo recibirá un puntero no válido. Use **THROW_LAST** para volver a iniciar `e`.

Para obtener más información, consulte [excepciones: detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Vea también

[Control de excepciones](../mfc/exception-handling-in-mfc.md)

