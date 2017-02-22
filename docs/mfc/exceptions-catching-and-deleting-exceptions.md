---
title: "Excepciones: Detectar y eliminar excepciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AND_CATCH (macro)"
  - "bloques catch, detectar y eliminar excepciones"
  - "control de excepciones, detectar y eliminar excepciones"
  - "excepciones, eliminar"
  - "ejecución, valores devueltos desde el bloque catch"
  - "control de excepciones try-catch, detectar y eliminar excepciones"
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Excepciones: Detectar y eliminar excepciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las instrucciones y los ejemplos siguientes muestran cómo detectar y eliminar excepciones.  Para obtener más información sobre **try**, **catch**, y las palabras clave de `throw` , vea [Control de excepciones de C\+\+](../cpp/cpp-exception-handling.md).  
  
 Los controladores de excepciones deben eliminar objetos de excepción que controlan, porque el error eliminar la excepción se produce una pérdida de memoria siempre que ese código detecte una excepción.  
  
 El bloque de **catch** debe eliminar una excepción cuando:  
  
-   El bloque de **catch** produce una nueva excepción.  
  
     Por supuesto, no debe eliminar la excepción si se produce la misma excepción de nuevo:  
  
     [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/CPP/exceptions-catching-and-deleting-exceptions_1.cpp)]  
  
-   La ejecución vuelve dentro del bloque de **catch** .  
  
> [!NOTE]
>  Al eliminar `CException`, utilice la función miembro de **Suprimir** para eliminar la excepción.  No utilice la palabra clave de **borrar** , porque puede fallar si la excepción no está en la pila.  
  
#### Para detectar y eliminar excepciones  
  
1.  Utilice la palabra clave de **try** para configurar un bloque de **try** .  Ejecute las instrucciones del programa que podría producir una excepción dentro de un bloque de **try** .  
  
     Utilice la palabra clave de **catch** para configurar un bloque de **catch** .  Coloque el código de control de excepciones en un bloque de **catch** .  El código del bloque de **catch** sólo se ejecuta si el código del bloque de **try** produce una excepción del tipo especificado en la instrucción de **catch** .  
  
     El esquema siguiente muestra cómo **try** y bloques de **catch** se organizan normalmente:  
  
     [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/CPP/exceptions-catching-and-deleting-exceptions_2.cpp)]  
  
     Cuando se produce una excepción, el control pasa a primer **catch** bloqueado cuya coincide con excepción\- declaración el tipo de la excepción.  Puede controlar los diferentes tipos de excepciones con bloques secuenciales de **catch** como se indica a continuación:  
  
     [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/CPP/exceptions-catching-and-deleting-exceptions_3.cpp)]  
  
 Para obtener más información, vea [Excepciones: El desarrollo de las macros MFC Exception](../mfc/exceptions-converting-from-mfc-exception-macros.md).  
  
## Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)