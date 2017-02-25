---
title: "Comparaci&#243;n de caracteres | Microsoft Docs"
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
  - "caracteres [C++], comparar"
  - "comparar caracteres"
  - "MBCS [C++], comparación de caracteres"
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 8
---
# Comparaci&#243;n de caracteres
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice las sugerencias siguientes:  
  
-   La comparación de un byte inicial conocido con un carácter ASCII funciona correctamente:  
  
    ```  
    if( *sz1 == 'A' )  
    ```  
  
-   La comparación de dos caracteres desconocidos requiere el uso de una de las macros definidas en Mbstring.h:  
  
    ```  
    if( !_mbccmp( sz1, sz2) )  
    ```  
  
     De este modo se garantiza que se compara la igualdad de los dos bytes de un carácter de doble byte.  
  
## Vea también  
 [Sugerencias de programación para MBCS](../Topic/MBCS%20Programming%20Tips.md)   
 [Desbordamiento de búfer](../text/buffer-overflow.md)