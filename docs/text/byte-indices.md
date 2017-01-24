---
title: "&#205;ndices de byte | Microsoft Docs"
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
  - "índices de byte [C++]"
  - "MBCS [C++], índices de byte"
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
caps.latest.revision: 7
caps.handback.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# &#205;ndices de byte
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice las sugerencias siguientes:  
  
-   El trabajo con un índice byte a byte en una cadena presenta problemas similares a los de la manipulación de punteros.  Observe este ejemplo, que examina una cadena con el carácter de barra inversa \(\\\):  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i++;  
    ```  
  
     Esto puede dar lugar a la indización de un byte final, en lugar de un byte inicial, y, por consiguiente, puede que no apunte a un `character`.  
  
-   Utilice la función [\_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md) para resolver el problema anterior:  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i += _mbclen ( rgch + i );  
    ```  
  
     De este modo, se indizará de forma correcta a un byte inicial, y, por consiguiente, a un `character`.  La función `_mbclen` determina el tamaño de un carácter \(1 o 2 bytes\).  
  
## Vea también  
 [Sugerencias de programación para MBCS](../Topic/MBCS%20Programming%20Tips.md)   
 [Último carácter de una cadena](../text/last-character-in-a-string.md)