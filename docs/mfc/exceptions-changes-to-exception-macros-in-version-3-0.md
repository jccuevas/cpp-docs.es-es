---
title: 'Excepciones: Cambios en las Macros de excepción en la versión 3.0 | Documentos de Microsoft'
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
ms.openlocfilehash: 1c4e6c7744c3d5328985eee24e67ee1eb359fb3c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931023"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Excepciones: Cambios en las macros de excepción en la versión 3.0
Se trata de un tema avanzado.  
  
 En la versión 3.0 y versiones posterior de MFC, las macros de control de excepciones han cambiado para usar las excepciones de C++. Este artículo explica cómo estos cambios pueden afectar al comportamiento del código existente que utiliza las macros.  
  
 En este artículo se tratan los siguientes temas:  
  
-   [Tipos de excepción y la macro CATCH](#_core_exception_types_and_the_catch_macro)  
  
-   [Volver a producir excepciones](#_core_re.2d.throwing_exceptions)  
  
##  <a name="_core_exception_types_and_the_catch_macro"></a> Tipos de excepción y la Macro CATCH  
 En versiones anteriores de MFC, la **CATCH** macro usa información de tipo en tiempo de ejecución MFC para determinar el tipo de una excepción; se determina el tipo de la excepción, en otras palabras, en el bloque catch. Con las excepciones de C++, sin embargo, el tipo de la excepción siempre viene determinado en el sitio de producción por el tipo del objeto de excepción que se produce. Esto causará incompatibilidades en el caso excepcional, donde el tipo del puntero al objeto iniciado difiere del tipo del objeto iniciado.  
  
 En el ejemplo siguiente se muestra el resultado de las diferencias entre la versión 3.0 de MFC y las versiones anteriores:  
  
 [!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]  
  
 Este código se comporta de manera diferente en la versión 3.0 porque el control siempre se pasa a la primera **catch** bloque con una declaración de excepción correspondiente. El resultado de la expresión throw  
  
 [!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]  
  
 se produce como un `CException*`, incluso si se crea como un `CCustomException`. El **CATCH** macro en MFC versiones 2.5 y anterior utiliza `CObject::IsKindOf` para probar el tipo en tiempo de ejecución. Dado que la expresión  
  
 [!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]  
  
 es true, el primer bloque catch detecta la excepción. En la versión 3.0, que usa las excepciones de C++ para implementar muchas de las macros de control de excepciones, el segundo bloque catch coincide con la produce `CException`.  
  
 Código parecido a esto es poco habitual. Normalmente aparece cuando se pasa un objeto de excepción a otra función que acepta un tipo genérico `CException*`realiza el procesamiento de "previo a throw" y, por último, se produce la excepción.  
  
 Para solucionar este problema, mueva la expresión throw desde la función al código de llamada y producirá una excepción del tipo real conocida por el compilador en el momento en que se generó la excepción.  
  
##  <a name="_core_re.2d.throwing_exceptions"></a> Volver a producir excepciones  
 Un bloque catch no puede producir el mismo puntero de excepción que detectó.  
  
 Por ejemplo, este código era válido en versiones anteriores, pero tendrá resultados inesperados con la versión 3.0:  
  
 [!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]  
  
 Usar **THROW** en la instrucción catch bloque hace que el puntero `e` va a eliminar, por lo que el sitio de la instrucción catch externa recibirá un puntero no válido. Use **THROW_LAST** para volver a producir `e`.  
  
 Para obtener más información, consulte [excepciones: detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)

