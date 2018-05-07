---
title: Compilador advertencia (nivel 4) C4205 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4205
dev_langs:
- C++
helpviewer_keywords:
- C4205
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc8c811fd8d67964bdef8149aea09d83e4649b99
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4205"></a>Advertencia del compilador (nivel 4) C4205
ha utilizado una extensión no estándar: declaración de función estática en el ámbito de función  
  
 Con las extensiones de Microsoft (/Ze), **estático** funciones se pueden declarar dentro de otra función. La función recibe un ámbito global.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4205.c  
// compile with: /W4  
void func1()  
{  
   static int func2();  // C4205  
};  
  
int main()  
{  
}  
```  
  
 Dichas inicializaciones no son válidas en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).