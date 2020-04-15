---
title: 'Excepciones: Detectar y eliminar excepciones'
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
ms.openlocfilehash: 74022c8bc6af1d2cdf74fa452d4e0483637e542e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365513"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Excepciones: Detectar y eliminar excepciones

Las siguientes instrucciones y ejemplos muestran cómo detectar y eliminar excepciones. Para obtener más información sobre las palabras clave **try**, **catch**y **throw,** consulte Prácticas recomendadas modernas de [C++, para obtener excepciones y control](../cpp/errors-and-exception-handling-modern-cpp.md)de errores.

Los controladores de excepciones deben eliminar los objetos de excepción que controlan, porque si no se elimina la excepción, se produce una pérdida de memoria cada vez que ese código detecta una excepción.

El bloque **catch** debe eliminar una excepción cuando:

- El bloque **catch** produce una nueva excepción.

   Por supuesto, no debe eliminar la excepción si vuelve a producir la misma excepción:

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- La ejecución vuelve desde dentro del bloque **catch.**

> [!NOTE]
> Al eliminar un `CException`, `Delete` utilice la función miembro para eliminar la excepción. No utilice la palabra clave **delete,** porque puede producir un error si la excepción no está en el montón.

#### <a name="to-catch-and-delete-exceptions"></a>Para detectar y eliminar excepciones

1. Utilice la palabra clave **try** para configurar un bloque **try.** Ejecute cualquier instrucción de programa que pueda producir una excepción dentro de un bloque **try.**

   Utilice la palabra clave **catch** para configurar un bloque **catch.** Coloque el código de control de excepciones en un bloque **catch.** El código del bloque **catch** solo se ejecuta si el código del bloque **try** produce una excepción del tipo especificado en la instrucción **catch.**

   El siguiente esqueleto muestra cómo los bloques **try** y **catch** se organizan normalmente:

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Cuando se produce una excepción, el control pasa al primer bloque **catch** cuya declaración de excepción coincide con el tipo de la excepción. Puede controlar selectivamente diferentes tipos de excepciones con bloques **catch** secuenciales como se indica a continuación:

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Para obtener más información, vea [Excepciones: conversión de](../mfc/exceptions-converting-from-mfc-exception-macros.md)macros de excepciones MFC .

## <a name="see-also"></a>Consulte también

[Control de excepciones](../mfc/exception-handling-in-mfc.md)
