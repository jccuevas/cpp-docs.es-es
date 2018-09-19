---
title: Comparación de caracteres | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 246801abcb04cc8d9c2fd1a005183501bde240d1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42612331"
---
# <a name="character-comparison"></a>Comparación de caracteres
Use las sugerencias siguientes:  
  
-   Comparación de un byte inicial conocido con un carácter ASCII funciona correctamente:  
  
    ```  
    if( *sz1 == 'A' )  
    ```  
  
-   Comparación de dos caracteres desconocidos requiere el uso de una de las macros definidas en Mbstring.h:  
  
    ```  
    if( !_mbccmp( sz1, sz2) )  
    ```  
  
     Esto garantiza que los bytes de un carácter de doble byte se comparan la igualdad.  
  
## <a name="see-also"></a>Vea también  
 [Sugerencias de programación para MBCS](../text/mbcs-programming-tips.md)   
 [Desbordamiento de búfer](../text/buffer-overflow.md)