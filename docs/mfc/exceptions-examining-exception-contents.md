---
title: "Excepciones: Examinar contenidos de excepciones | Microsoft Docs"
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
  - "bloques catch, excepciones de la función MFC"
  - "CException (clase), excepciones de clase"
  - "control de excepciones, MFC"
  - "producir excepciones, contenido de excepción"
  - "control de excepciones try-catch, contenido de excepción"
  - "control de excepciones try-catch, excepciones de la función MFC"
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Excepciones: Examinar contenidos de excepciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Aunque el argumento de un bloque de **catch** puede ser de casi cualquier tipo de datos, las funciones de MFC producen excepciones de los tipos derivados de la clase `CException`.  Para detectar una excepción producida por una función de MFC, a continuación, escribe **catch** bloqueado cuyo argumento es un puntero a un objeto de `CException` \(o a un objeto derivado de `CException`, como `CMemoryException`\).  Dependiendo del tipo exacto de la excepción, puede examinar los miembros de datos del objeto de excepción al recopilar información sobre la causa concreta de la excepción.  
  
 Por ejemplo, el tipo de `CFileException` tiene el miembro de datos de `m_cause` , que contiene un tipo enumerado que especifique la causa de la excepción de archivo.  Algunos ejemplos de valores devueltos son **CFileException::fileNotFound** y **CFileException::readOnly**.  
  
 El ejemplo siguiente se muestra cómo examinar el contenido de `CFileException`.  Otros tipos de excepción pueden ser examinados similar.  
  
 [!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/CPP/exceptions-examining-exception-contents_1.cpp)]  
  
 Para obtener más información, vea [Excepciones: Liberar objetos de Excepciones](../mfc/exceptions-freeing-objects-in-exceptions.md) y [Excepciones: Detectando y eliminar Excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)