---
title: Error irrecuperable C1094 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1094
dev_langs:
- C++
helpviewer_keywords:
- C1094
ms.assetid: 9e1193b2-cb95-44f9-bf6f-019e0d41dd97
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 630ed1979656351f6816ac5c24a7cbe386e62cce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1094"></a>Error irrecuperable C1094
'-Zmval1': opción de línea de comandos no es coherente con el valor utilizado para generar el encabezado precompilado ('-Zmval2')  
  
 El valor que se pasa a [/Yc](../../build/reference/yc-create-precompiled-header-file.md) debe ser el mismo valor que se pasa a [/Yu](../../build/reference/yu-use-precompiled-header-file.md) (**/Zm** valores deben ser iguales en todas las compilaciones que usan o crean el mismo precompilados archivo de encabezado).  
  
 El ejemplo siguiente genera C1094:  
  
```  
// C1094.h  
int func1();  
```  
  
 Y luego,  
  
```  
// C1094.cpp  
// compile with: /Yc"C1094.h" /Zm200  
int u;  
int main() {  
   int sd = 32;  
}  
#include "C1094.h"  
```  
  
 Y luego,  
  
```  
// C1094b.cpp  
// compile with: /Yu"C1094.h" /Zm300 /c  
#include "C1094.h"   // C1094 compile with /Zm200  
void Test() {}  
```