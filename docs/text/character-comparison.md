---
title: Comparación de caracteres | Documentos de Microsoft
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b969783a19c0836a8ab81d75820fc688df3ef31e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
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