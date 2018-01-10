---
title: "Índices de byte | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 594acadeedad06e9720180c38bd0bcd657391879
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="byte-indices"></a>Índices de byte
Utilice las siguientes sugerencias:  
  
-   Trabajar con un índice byte a byte en una cadena presenta problemas similares a los que supone la manipulación de punteros. Considere este ejemplo, que busca una cadena con un carácter de barra diagonal inversa:  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i++;  
    ```  
  
     Esto podría la indización de un byte final, en lugar de un byte inicial, y, por tanto, no puede señalar a un `character`.  
  
-   Use la [_mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md) función para resolver el problema anterior:  
  
    ```  
    while ( rgch[ i ] != '\\' )  
        i += _mbclen ( rgch + i );  
    ```  
  
     Esto se indiza correctamente a un byte inicial, por lo tanto, para un `character`. El `_mbclen` función determina el tamaño de un carácter (1 o 2 bytes).  
  
## <a name="see-also"></a>Vea también  
 [Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)   
 [Último carácter de una cadena](../text/last-character-in-a-string.md)