---
title: "Comparación de caracteres | Documentos de Microsoft"
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
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28c2cd3a2e868a595d73d06b5cae8e71ec8cc313
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="character-comparison"></a>Comparación de caracteres
Utilice las siguientes sugerencias:  
  
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