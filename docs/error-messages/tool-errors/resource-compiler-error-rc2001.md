---
title: "Error del compilador de recursos RC2001 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC2001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2001"
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador de recursos RC2001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

nueva línea en constante  
  
 Una constante de cadena continuó en una segunda línea sin una barra diagonal inversa \(**\\**\) o signos de comillas tipográficas \(**"**\) de cierre o de apertura.  
  
 Para dividir una constante de cadena que ocupa dos líneas en el archivo de código fuente, tiene dos opciones:  
  
-   Terminar la primera línea con el carácter de continuación de línea, una barra diagonal inversa.  
  
-   Cerrar la cadena en la primera línea con un signo de comillas tipográficas y abrir la cadena de la línea siguiente con otro signo de comillas tipográficas.  
  
 No basta con cerrar la primera línea con \\n, la secuencia de escape para incrustar un carácter de nueva línea en una constante de cadena.