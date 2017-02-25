---
title: "Alternativas de entrada/salida | Microsoft Docs"
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
  - "E/S [C++], alternativas"
ms.assetid: 9f8401c7-d90d-4285-8918-63573df74a80
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Alternativas de entrada/salida
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ proporciona varias alternativas para la programación de E\/S:  
  
-   Biblioteca en tiempo de ejecución directa, E\/S inseparada de C.  
  
-   E\/S de secuencia de la biblioteca en tiempo de ejecución de ANSI C.  
  
-   E\/S directa de la consola y el puerto.  
  
-   Biblioteca MFC \(Microsoft Foundation Class\).  
  
-   Biblioteca estándar de Microsoft C\+\+.  
  
 Las clases iostream son útiles para almacenado en búfer, E\/S de texto con formato.  También son útiles para E\/S inseparada o binaria si necesita la interfaz de programación de c\+\+. y decide no utilizar la biblioteca de \(MFC\) de la clase de la Microsoft foundation class.  Las clases iostream son una alternativa orientada a objetos de E\/S a funciones en tiempo de ejecución de C.  
  
 Puede utilizar clases iostream con el sistema operativo Microsoft Windows.  Las secuencias de la cadena y el archivo funcionan sin restricciones, pero los objetos de secuencia `cin`, `cout`, `cerr`, y `clog` de modo de carácter son incoherentes con la interfaz gráfica de usuario de Windows.  También puede derivar las clases personalizadas de secuencia que interactúan directamente con el entorno de Windows.  
  
## Vea también  
 [¿Qué es un flujo?](../standard-library/what-a-stream-is.md)