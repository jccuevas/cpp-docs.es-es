---
title: Compilador advertencia (nivel 1) C4218 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4218
dev_langs:
- C++
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88b27af84c390760274bb20665eec4452c8e7072
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4218"></a>Advertencia del compilador (nivel 1) C4218
ha utilizado una extensión no estándar: debe especificar al menos una clase de almacenamiento o un tipo  
  
 Con las extensiones de Microsoft (/Ze), puede declarar una variable sin especificar una clase de almacenamiento o tipo. El tipo predeterminado es `int`.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4218.c  
// compile with: /W4  
i;  // C4218  
  
int main()  
{  
}  
```  
  
 Estas declaraciones no son válidas en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).