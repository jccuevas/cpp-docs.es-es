---
title: Error del compilador C2217 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2217
dev_langs:
- C++
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 0f1795534af1332859fd1a33a137573df82643b4
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2217"></a>Error del compilador C2217
'atributo1' requiere 'atributo2'  
  
 El primer atributo de función requiere el segundo atributo.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Interrumpir (`__interrupt`) función declarada como `near`. Interrumpir las funciones deben ser `far`.  
  
2.  Interrumpir la función declarada con `__stdcall`, o `__fastcall`. Funciones de interrupción debe usar C convenciones de llamada.  
  
## <a name="example"></a>Ejemplo  
 El error C2217 también puede producirse si intenta enlazar a un delegado a una función CLR que toma un número variable de argumentos. Si la función también tiene sobrecarga de matriz param e, utilice en su lugar. El ejemplo siguiente genera el error C2217.  
  
```  
// C2217.cpp  
// compile with: /clr  
using namespace System;  
delegate void MyDel(String^, Object^, Object^, ...);   // C2217  
delegate void MyDel2(String ^, array<Object ^> ^);   // OK  
  
int main() {  
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);  
   array<Object ^ > ^ x = gcnew array<Object ^>(2);  
   x[0] = safe_cast<Object^>(0);  
   x[1] = safe_cast<Object^>(1);  
  
   // wl("{0}, {1}", 0, 1);  
   wl("{0}, {1}", x);  
}  
```
