---
title: Compilador advertencia (nivel 1) C4325 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4325
dev_langs:
- C++
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 936433987f823ae7d5d22cfd075f188dd5d4b1e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277649"
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