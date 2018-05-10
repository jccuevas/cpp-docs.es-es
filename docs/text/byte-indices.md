---
title: Índices de byte | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 509e66c7ea458519eaa9dc4f52c8a6b65c789d0f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
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