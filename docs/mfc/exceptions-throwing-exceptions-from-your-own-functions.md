---
title: "Excepciones: Iniciar excepciones desde sus propias funciones | Microsoft Docs"
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
  - "excepciones, iniciar"
  - "funciones [C++], producir excepciones"
  - "producir excepciones, desde funciones"
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Excepciones: Iniciar excepciones desde sus propias funciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Es posible utilizar el paradigma de control de excepciones de MFC sólo para detectar las excepciones producidas por funciones en MFC u otras bibliotecas.  Además de detectar excepciones producidas por código de biblioteca, puede producir excepciones del propio código si escribe las funciones que pueden encontrar condiciones excepcionales.  
  
 Cuando se produce una excepción, la ejecución de la función actual se detiene y salta directamente al bloque de **catch** del marco más interno de la excepción.  El mecanismo de excepción omite la ruta normal del resultado de una función.  Por consiguiente, asegúrese de eliminar los bloques de memoria que se eliminarán en una salida normal.  
  
#### Para producir una excepción  
  
1.  El uso uno auxiliares de MFC funciona, por ejemplo `AfxThrowMemoryException`.  Estas funciones producen un objeto de excepción reservado del tipo adecuado.  
  
     En el ejemplo siguiente, una función intenta asignar dos bloques de memoria y produce una excepción si se produce un error en cualquier asignación:  
  
     [!code-cpp[NVC_MFCExceptions#17](../mfc/codesnippet/CPP/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]  
  
     Si la primera asignación, puede producir simplemente la excepción de memoria insuficiente.  Si la primera asignación es correcta pero segunda falla, debe liberar la primera asignación bloqueada antes de iniciar la excepción.  Si ambas asignaciones tienen éxito, puede continuar normalmente y liberar los bloques al salir de la función.  
  
     O bien  
  
2.  Utilice una excepción definida por el usuario para indicar una condición del problema.  Puede producir un elemento de cualquier tipo, incluso una clase completa, como la excepción.  
  
     El ejemplo siguiente se intenta reproducir un sonido a través de un dispositivo de ondas y produce una excepción si se produce un error.  
  
     [!code-cpp[NVC_MFCExceptions#18](../mfc/codesnippet/CPP/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]  
  
> [!NOTE]
>  El control predeterminado de MFC de excepciones sólo se aplica a los punteros a objetos de `CException` \(y los objetos de `CException`\- clases derivadas\).  El ejemplo anterior omite el mecanismo de excepción de MFC.  
  
## Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)