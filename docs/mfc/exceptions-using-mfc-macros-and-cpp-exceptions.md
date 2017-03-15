---
title: "Excepciones: Usar macros de MFC y excepciones de C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bloques catch, eliminar código explícitamente en"
  - "bloques catch, mixtos"
  - "control de excepciones, MFC"
  - "control de excepciones, varios lenguajes"
  - "objetos de excepción"
  - "objetos de excepción, eliminar"
  - "excepciones, macros de MFC frente a palabras clave de C++"
  - "daños en el montón"
  - "pérdidas de memoria, objeto de excepción no eliminado"
  - "bloques catch anidados"
  - "bloques Try anidados"
  - "control de excepciones try-catch, mezclar macros MFC y palabras clave C++"
  - "control de excepciones try-catch, bloques Try anidados"
ms.assetid: d664a83d-879b-44d4-bdf0-029f0aca69e9
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Excepciones: Usar macros de MFC y excepciones de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este artículo trata sobre las consideraciones para escribir código que utilice las macros de control de excepciones de MFC y las palabras clave de control de excepciones de C\+\+.  
  
 En este artículo se tratan los siguientes temas:  
  
-   [Mezclar palabras clave y macros de excepción](#_core_mixing_exception_keywords_and_macros)  
  
-   [Bloque Try dentro de los bloques catch](#_core_try_blocks_inside_catch_blocks)  
  
##  <a name="_core_mixing_exception_keywords_and_macros"></a> Mezclar las palabras clave y macros de Excepciones  
 Puede mezclar palabras clave de las macros de excepción de MFC y de excepciones de C\+\+ en el mismo programa.  Pero no puede mezclar las macros MFC con palabras clave de excepciones de C\+\+ en el mismo bloque porque macros eliminan objetos de excepción automáticamente cuando salen del ámbito, aunque no hace el código mediante las palabras clave excepción\- que administran.  Para obtener más información, vea el artículo [Excepciones: Detectando y eliminar Excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
 La diferencia principal entre macros de y las palabras clave es que las macros “automáticamente” cancelar una excepción detectada cuando la excepción sale del ámbito.  El código mediante las palabras clave no tiene; las excepciones detectadas en un bloque catch deben en se eliminarán.  Mezclar palabras clave de macros y de excepciones de C\+\+ puede provocar pérdidas de memoria cuando un objeto de excepción no se elimina, o daños en la pila cuando una excepción se elimina dos veces.  
  
 El código siguiente, por ejemplo, reemplaza el puntero de la excepción:  
  
 [!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/CPP/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]  
  
 El problema se produce porque se elimina `e` cuando la ejecución del bloque “interno” de **CATCH** .  Mediante la macro de `THROW_LAST` en lugar de la instrucción de **THROW** hará el bloque “externo” de **CATCH** para recibir un puntero válido:  
  
 [!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/CPP/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]  
  
##  <a name="_core_try_blocks_inside_catch_blocks"></a> Bloque Try dentro de los bloques Catch  
 No puede re\- captura la excepción actual dentro de **try** bloqueado que está dentro de un bloque de **CATCH** .  El ejemplo siguiente no es válido:  
  
 [!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/CPP/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]  
  
 Para obtener más información, vea [Excepciones: Contenido de inspección de excepción](../mfc/exceptions-examining-exception-contents.md).  
  
## Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)