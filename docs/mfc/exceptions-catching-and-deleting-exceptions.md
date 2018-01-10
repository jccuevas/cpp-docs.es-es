---
title: 'Excepciones: Detectar y eliminar excepciones | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8496b5228fe4002bb1ca80f8fbe793fd5e16ca81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Excepciones: Detectar y eliminar excepciones
Las instrucciones y los ejemplos siguientes muestran cómo detectar y eliminar excepciones. Para obtener más información sobre la **intente**, **catch**, y `throw` palabras clave, consulte [control de excepciones de C++](../cpp/cpp-exception-handling.md).  
  
 Los controladores de excepciones deben eliminar objetos de excepción que controlan, porque si no se elimina la excepción produce una pérdida de memoria siempre que ese código detecta una excepción.  
  
 Su **catch** bloque debe eliminar una excepción cuando:  
  
-   El **catch** bloque produce una nueva excepción.  
  
     Por supuesto, no debe eliminar la excepción si se produce la misma excepción:  
  
     [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]  
  
-   Ejecución devuelve desde el **catch** bloque.  
  
> [!NOTE]
>  Cuando se elimina un `CException`, use la **eliminar** función de miembro para eliminar la excepción. No utilice la **eliminar** (palabra clave), porque se puede producir un error si la excepción no está en el montón.  
  
#### <a name="to-catch-and-delete-exceptions"></a>Para detectar y eliminar excepciones  
  
1.  Use la **intente** palabra clave que se va a configurar un **intente** bloque. Ejecutar las instrucciones de programa que podrían producir una excepción dentro de un **intente** bloque.  
  
     Use la **catch** palabra clave que se va a configurar un **catch** bloque. Coloque el código de control de excepciones en un **catch** bloque. El código en el **catch** bloque se ejecuta sólo si el código dentro de la **intente** bloque produce una excepción del tipo especificado en el **catch** instrucción.  
  
     El esquema siguiente se muestra cómo **intente** y **catch** bloques se organizan normalmente:  
  
     [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]  
  
     Cuando se produce una excepción, el control pasa a la primera **catch** bloque cuya declaración de excepción coincide con el tipo de la excepción. Puede controlar selectivamente diferentes tipos de excepciones con secuencial **catch** bloquea como se muestra a continuación:  
  
     [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]  
  
 Para obtener más información, consulte [excepciones: convertir desde Macros de excepción de MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)

