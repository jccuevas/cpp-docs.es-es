---
title: Error del compilador C3828 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3828
dev_langs:
- C++
helpviewer_keywords:
- C3828
ms.assetid: 8d9cee75-9504-4bc8-88b6-2413618a3f45
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 1b2dfaa6e0c414c80122bcb4291bb021bc1f3c74
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3828"></a>Error del compilador C3828
'tipo de objeto': no se permiten al crear instancias de administrado argumentos de ubicación o WinRTclasses  
  
 Cuando se crea un objeto de un tipo administrado o en tiempo de ejecución de Windows, no puede usar el formato de selección de ubicación del operador [gcnew nueva, ref](../../windows/ref-new-gcnew-cpp-component-extensions.md) o [nueva](../../cpp/new-operator-cpp.md).  
  
 El ejemplo siguiente genera el error C3828 y muestra cómo corregirlo:  
  
```  
// C3828a.cpp  
// compile with: /clr  
ref struct M {  
};  
  
ref struct N {  
   static array<char>^ bytes = gcnew array<char>(256);  
};  
  
int main() {  
   M ^m1 = new (&N::bytes) M();   // C3828  
   // The following line fixes the error.  
   // M ^m1 = gcnew M();  
}  
```
