---
title: "&#218;ltimo car&#225;cter de una cadena | Microsoft Docs"
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
  - "último carácter de una cadena"
  - "MBCS [C++], último carácter de una cadena"
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# &#218;ltimo car&#225;cter de una cadena
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice las sugerencias siguientes:  
  
-   Los intervalos de bytes finales y el juego de caracteres ASCII se superponen en muchos casos.  Se pueden utilizar de forma segura búsquedas byte a byte para cualquier carácter de control \(menor que 32\).  
  
-   Observe la siguiente línea de código, que podría estar comprobando si el último carácter de una cadena es un carácter de barra inversa:  
  
    ```  
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?  
        // . . .  
    ```  
  
     Como `strlen` no está preparado para MBCS, se devuelve el número de bytes, no el número de caracteres, en una cadena multibyte.  También conviene tener en cuenta que, en algunas páginas de códigos \(932, por ejemplo\), '\\' \(0x5c\) es un byte final válido \(`sz` es una cadena de C\).  
  
     Una posible solución consiste en volver a crear el código del modo siguiente:  
  
    ```  
    char *pLast;  
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz  
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )  
        // . . .  
    ```  
  
     Este código utiliza las funciones MBCS `_mbsrchr` y `_mbsinc`.  Dado que estas funciones están preparadas para MBCS, pueden distinguir entre un carácter '\\' y un byte final '\\'.  El código realiza alguna acción si el último carácter de la cadena es un valor nulo \('\\0'\).  
  
## Vea también  
 [Sugerencias de programación para MBCS](../Topic/MBCS%20Programming%20Tips.md)   
 [Asignación de caracteres](../text/character-assignment.md)