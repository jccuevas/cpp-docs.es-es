---
title: Compilador advertencia (nivel 1) C4325 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4325
dev_langs:
- C++
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ab31150efc02601d7392470198e162e979ac4917
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4325"></a>Advertencia del compilador (nivel 1) C4325
**atributos para la sección estándar '**   
 ***sección* ' omite**  
  
 No puede cambiar los atributos de una sección estándar. Por ejemplo:  
  
```  
#pragma section(".sdata", long)  
```  
  
 Esto reemplazaría el `.sdata` sección estándar que utiliza el **corto** tipo de datos con la **largo** tipo de datos.  
  
 Incluyen secciones estándares cuyos atributos no se pueden cambiar,  
  
-   .Data  
  
-   .sdata  
  
-   BSS  
  
-   .sbss  
  
-   Text  
  
-   .const  
  
-   .sconst  
  
-   rdata  
  
-   .srdata  
  
 Las secciones adicionales se pueden agregar más adelante.  
  
## <a name="see-also"></a>Vea también  
 [section](../../preprocessor/section.md)