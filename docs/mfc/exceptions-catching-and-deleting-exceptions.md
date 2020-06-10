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
ms.openlocfilehash: 50e3a3f8c064b2a054f0018e87c4e8782a5dc363
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618846"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Excepciones: Detectar y eliminar excepciones

En las siguientes instrucciones y ejemplos se muestra cómo detectar y eliminar excepciones. Para obtener más información sobre las palabras clave **try**, **catch**y **Throw** , vea [procedimientos recomendados de C++ moderno para excepciones y control de errores](../cpp/errors-and-exception-handling-modern-cpp.md).

Los controladores de excepciones deben eliminar los objetos de excepción que administran, porque si no se elimina la excepción, se produce una fuga de memoria cada vez que el código detecta una excepción.

El bloque **catch** debe eliminar una excepción cuando:

- El bloque **catch** produce una nueva excepción.

   Por supuesto, no debe eliminar la excepción si vuelve a producir la misma excepción:

   [!code-cpp[NVC_MFCExceptions#3](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- La ejecución se devuelve desde dentro del bloque **catch** .

> [!NOTE]
> Al eliminar `CException` , utilice la `Delete` función miembro para eliminar la excepción. No utilice la palabra clave **Delete** , ya que se puede producir un error si la excepción no está en el montón.

#### <a name="to-catch-and-delete-exceptions"></a>Para detectar y eliminar excepciones

1. Use la palabra clave **try** para configurar un bloque **try** . Ejecute cualquier instrucción de programa que pueda producir una excepción dentro de un bloque **try** .

   Use la palabra clave **catch** para configurar un bloque **catch** . Coloque el código de control de excepciones en un bloque **catch** . El código del bloque **catch** solo se ejecuta si el código incluido en el bloque **try** produce una excepción del tipo especificado en la instrucción **catch** .

   El esqueleto siguiente muestra cómo se organizan normalmente los bloques **try** y **catch** :

   [!code-cpp[NVC_MFCExceptions#4](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Cuando se produce una excepción, el control pasa al primer bloque **catch** cuya declaración de excepción coincide con el tipo de la excepción. Puede controlar de forma selectiva distintos tipos de excepciones con bloques **catch** secuenciales, como se muestra a continuación:

   [!code-cpp[NVC_MFCExceptions#5](codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Para obtener más información, vea [excepciones: convertir desde macros de excepción de MFC](exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Consulte también

[Control de excepciones](exception-handling-in-mfc.md)
