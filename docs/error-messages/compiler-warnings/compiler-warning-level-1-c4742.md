---
title: Compilador advertencia (nivel 1) C4742 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4742
dev_langs:
- C++
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9c5c891699e89b177f9a3c070a95f496e2c77ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4742"></a>Advertencia del compilador (nivel 1) C4742
'var' tiene una alineación diferente en 'archivo1' y 'archivo2': número y número  
  
 Una variable externa que se haga referencia o definida en dos archivos tiene diferente alineación en dichos archivos. Esta advertencia se genera cuando el compilador encuentra que `__alignof` para la variable en *file1* difiere de `__alignof` para la variable en *archivo2*. Esto puede deberse mediante tipos incompatibles al declarar variables en archivos diferentes, o mediante el uso de no coincidencia de `#pragma pack` en archivos diferentes.  
  
 Para resolver esta advertencia, utilice la misma definición de tipo o use nombres diferentes para las variables.  
  
 Para obtener más información, consulte [pack](../../preprocessor/pack.md) y [operador __alignof](../../cpp/alignof-operator.md).  
  
## <a name="example"></a>Ejemplo  
 Este es el primer archivo que define el tipo.  
  
```  
// C4742a.c  
// compile with: /c  
struct X {  
   char x, y, z, w;  
} global;  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4742.  
  
```  
// C4742b.c  
// compile with: C4742a.c /W1 /GL  
// C4742 expected  
extern struct X {  
   int a;  
} global;  
  
int main() {  
   global.a = 0;  
}  
```