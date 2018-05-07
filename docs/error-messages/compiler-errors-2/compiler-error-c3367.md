---
title: Error del compilador C3367 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3367
dev_langs:
- C++
helpviewer_keywords:
- C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2884e38d1ad1aecef8e7b0723674ebd9849d8f40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3367"></a>Error del compilador C3367
'función_miembro_estática': no se puede usar la función estática para crear un delegado sin enlazar.  
  
Cuando se llama a un delegado sin enlazar, debe pasar una instancia de un objeto. Puesto que se llama a una función miembro estática a través del nombre de clase, solo puede crear una instancia de un delegado sin enlazar con una función miembro de instancia.  
  
Para obtener más información acerca de delegados sin enlazar, vea [Cómo: definir y utilizar delegados (C++ / CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md).  
  
## <a name="example"></a>Ejemplo  
El ejemplo siguiente genera la advertencia C3367.  
  
```cpp  
// C3367.cpp  
// compile with: /clr  
ref struct R {  
   void b() {}  
   static void f() {}  
};  
  
delegate void Del(R^);  
  
int main() {  
   Del ^ a = gcnew Del(&R::b);   // OK  
   Del ^ b = gcnew Del(&R::f);   // C3367  
}  
```