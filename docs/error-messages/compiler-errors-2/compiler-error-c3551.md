---
title: Error del compilador C3551 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3551
dev_langs:
- C++
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f9f69adcf071415d3c1760294bdaaaec7b71f8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3551"></a>Error del compilador C3551
"se espera un tipo de valor devuelto especificado en tiempo de ejecución"  
  
 Si utiliza la palabra clave `auto` como marcador de posición del tipo de valor devuelto de una función, debe facilitar un tipo de valor devuelto especificado en tiempo de ejecución. En el ejemplo siguiente, el tipo de valor devuelto especificado en tiempo de ejecución de la función `myFunction` es un puntero a una matriz de cuatro elementos de tipo `int`.  
  
```  
auto myFunction()->int(*)[4];   
```  
  
## <a name="see-also"></a>Vea también  
 [auto](../../cpp/auto-cpp.md)