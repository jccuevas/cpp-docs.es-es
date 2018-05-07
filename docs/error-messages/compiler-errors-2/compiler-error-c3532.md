---
title: Error del compilador C3532 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3532
dev_langs:
- C++
helpviewer_keywords:
- C3532
ms.assetid: 51067853-eda8-4f59-86e8-8924e16d3a95
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1efce6659f8d848b47f0c4194b6420177ffad194
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3532"></a>Error del compilador C3532
'type': uso incorrecto de 'auto'  
  
 No se puede declarar el tipo indicado con el `auto` palabra clave. Por ejemplo, no puede usar el `auto` palabra clave para declarar una matriz o un método de tipo de valor devuelto.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Asegúrese de que la expresión de inicialización genera un tipo válido.  
  
2.  Asegúrese de que no se declara una matriz o un tipo de valor devuelto del método.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera el error C3532 porque el `auto` palabra clave no puede declarar un tipo de valor devuelto del método.  
  
```  
// C3532a.cpp  
// Compile with /Zc:auto  
auto f(){}   // C3532  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera el error C3532 porque el `auto` palabra clave no puede declarar una matriz.  
  
```  
// C3532b.cpp  
// Compile with /Zc:auto  
int main()  
{  
   int x[5];  
   auto a[5];            // C3532  
   auto b[1][2];         // C3532  
   auto y[5] = x;        // C3532  
   auto z[] = {1, 2, 3}; // C3532  
   auto w[] = x;         // C3532  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Auto (palabra clave)](../../cpp/auto-keyword.md)