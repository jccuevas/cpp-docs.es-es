---
title: "Último carácter de una cadena | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7b766bec977f35f9f346723cbaf3f62e48c8c878
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="last-character-in-a-string"></a>Último carácter de una cadena
Utilice las siguientes sugerencias:  
  
-   Traza de los intervalos de bytes superponen el juego en muchos casos de caracteres ASCII. Puede utilizar de forma segura búsquedas byte a byte para cualquier carácter de control (menor que 32).  
  
-   Tenga en cuenta la siguiente línea de código, que puede comprobar para ver si el último carácter de una cadena es un carácter de barra diagonal inversa:  
  
    ```  
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?  
        // . . .  
    ```  
  
     Dado que `strlen` no es compatible con MBCS, devuelve el número de bytes, no el número de caracteres, en una cadena multibyte. Además, tenga en cuenta que en algunas páginas de códigos (932, por ejemplo), '\\' (0x5c) es un byte final válido (`sz` es una cadena de C).  
  
     Una posible solución es volver a escribir el código de esta manera:  
  
    ```  
    char *pLast;  
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz  
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )  
        // . . .  
    ```  
  
     Este código utiliza las funciones MBCS `_mbsrchr` y `_mbsinc`. Dado que estas funciones están preparadas para MBCS, pueden distinguir entre un '\\'caracteres y un byte final'\\'. El código realiza alguna acción si el último carácter de la cadena es un valor nulo ('\0').  
  
## <a name="see-also"></a>Vea también  
 [Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)   
 [Asignación de caracteres](../text/character-assignment.md)