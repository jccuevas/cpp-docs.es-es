---
title: Error del compilador C2804 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2804
dev_langs:
- C++
helpviewer_keywords:
- C2804
ms.assetid: b066e563-cca4-450c-8ba7-3b0d7a89f3ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47a0c9a785ae47e6df00b1303553228521d20d00
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236612"
---
# <a name="compiler-error-c2804"></a>Error del compilador C2804
'operator operator' binario tiene demasiados parámetros  
  
 La función miembro del operador binario sobrecargado se declara con más de un parámetro. El primer parámetro de operando de una función miembro de operador binario, cuyo tipo es el tipo envolvente del operador, está implícito.  
  
## <a name="example"></a>Ejemplo  
 La muestra siguiente genera el error C2804 y muestra cómo corregirlo.  
  
```  
// C2804.cpp  
// compile by using: cl /c /W4 C2804.cpp  
class X {  
public:  
   X& operator+= (const X &left, const X &right);   // C2804  
   X& operator+= (const X &right);   // OK - left operand implicitly *this  
};  
  
int main() {  
   X x, y;  
   x += y;   // equivalent to x.operator+=(y)  
}  
```  
  
## <a name="example"></a>Ejemplo  
 La muestra siguiente genera el error C2804 y muestra cómo corregirlo.  
  
```  
// C2804_2.cpp  
// compile with: /clr /c  
ref struct Y {  
   Y^ operator +(Y^ hY, int i);   // C2804  
   static Y^ operator +(Y^ hY, int i);   // OK  
   Y^ operator +(int i);   // OK  
};  
```