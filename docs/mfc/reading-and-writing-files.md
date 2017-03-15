---
title: "Leer y escribir en archivos | Microsoft Docs"
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
  - "CFile (clase), objetos"
  - "CFile (clase), leer y escribir objetos CFile"
  - "ejemplos [MFC], leer archivos"
  - "ejemplos [MFC], escribir en archivos"
  - "archivos [C++], leer"
  - "archivos [C++], escribir"
  - "MFC [C++], operaciones en archivo"
  - "leer archivos"
  - "escribir en archivos [C++]"
ms.assetid: cac0c826-ba56-495f-99b3-ce6336f65763
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Leer y escribir en archivos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si utiliza las funciones archivo \(el archivo que administraban de la biblioteca en tiempo de ejecución de C, MFC que lee y escribir operaciones aparecerá familiar.  En este artículo se describe el leer directamente de y el escribir directamente a un objeto de `CFile` .  También puede hacer E\/S almacenado en búfer de archivo con la clase de [CArchive](../mfc/reference/carchive-class.md) .  
  
#### Para leer y escribir en el archivo  
  
1.  Use las funciones miembro de **de lectura** y de **Escribir** a leer y escribir datos en el archivo.  
  
     O bien  
  
2.  La función miembro de `Seek` también está disponible para desplazarse a un desplazamiento concreto dentro del archivo.  
  
 **de lectura** contiene un puntero a un búfer y el número de bytes para leer y devuelve el número de bytes real que se leyeron.  Si el número de bytes necesario no se ha podido leer porque se alcanza \(EOF\) final de archivo, el número real de bytes leídos se devuelve.  Si cualquier error de lectura aparece, se produce una excepción.  **Escribir** es similar a **de lectura**, pero el número de bytes escritos no se devuelve.  Si un error de escritura aparece, incluida la escritura de todos los bytes especificados, se produce una excepción.  Si tiene un objeto válido de `CFile` , puede leer de o utilizando como se muestra en el ejemplo siguiente:  
  
 [!code-cpp[NVC_MFCFiles#2](../mfc/codesnippet/CPP/reading-and-writing-files_1.cpp)]  
  
> [!NOTE]
>  Debe realizar normalmente operaciones de entrada\/salida dentro de un bloque de control de excepciones de **try**\/de**catch** .  Para obtener más información, vea [Control de excepciones \(MFC\)](../mfc/exception-handling-in-mfc.md).  
  
## Vea también  
 [Archivos](../mfc/files-in-mfc.md)