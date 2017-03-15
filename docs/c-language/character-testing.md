---
title: "Pruebas de caracteres | Microsoft Docs"
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
ms.assetid: 376ba061-bae3-427e-9569-33fa5949a199
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Pruebas de caracteres
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.3.1** Los juegos de caracteres probados por las funciones `isalnum`, `isalpha`, `iscntrl`, `islower`, `isprint` e `isupper`  
  
 La lista siguiente describe estas funciones tal como las implementa el compilador de Microsoft C.  
  
|Función|Prueba|  
|-------------|------------|  
|`isalnum`|Los caracteres 0 – 9, A–Z, a–z ASCII 48–57, 65–90, 97–122|  
|`isalpha`|Los caracteres A–Z, a–z ASCII 65–90, 97–122|  
|`iscntrl`|ASCII 0 –31, 127|  
|`islower`|Los caracteres a–z ASCII 97–122|  
|`isprint`|Los caracteres A–Z, a–z, 0 – 9, puntuación, espacio ASCII 32–126|  
|`isupper`|Los caracteres A–Z ASCII 65–90|  
  
## Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)