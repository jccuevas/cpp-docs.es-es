---
title: Compilador advertencia (nivel 3) C4267 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4267
dev_langs:
- C++
helpviewer_keywords:
- C4267
ms.assetid: 2fa2f13f-fa4f-47bb-ad8f-6cb19cfc91e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de75c4eb05002f638e6b665a39f2a35e114b0ab4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4267"></a>Advertencia del compilador (nivel 3) C4267
'var': conversión de 'size_t' a 'type'; posible pérdida de datos  
  
 El compilador detectó una conversión de `size_t` a un tipo más pequeño.  
  
 Para corregir esta advertencia, use `size_t` en lugar de `type`. También puede usar un tipo entero que sea al menos tan grande como `size_t`.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C4267.  
  
```  
// C4267.cpp  
// compile by using: cl /W4 C4267.cpp  
void Func1(short) {}  
void Func2(int) {}  
void Func3(long) {}  
void Func4(size_t) {}  
  
int main() {  
   size_t bufferSize = 10;  
   Func1(bufferSize);   // C4267 for all platforms  
   Func2(bufferSize);   // C4267 only for 64-bit platforms  
   Func3(bufferSize);   // C4267 only for 64-bit platforms  
   Func4(bufferSize);   // OK for all platforms  
}  
```