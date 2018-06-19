---
title: Error del compilador C2885 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2885
dev_langs:
- C++
helpviewer_keywords:
- C2885
ms.assetid: 7743e5f3-a034-44b4-9ee8-5a6254c27f8c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f37ea0f9fadb74b44eea5ad110f7f12b884f0e41
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244177"
---
# <a name="compiler-error-c2885"></a>Error del compilador C2885
'Class:: identifier': no es una declaración using válida en un ámbito no clase  
  
 Se usa un [con](../../cpp/using-declaration.md) declaración incorrectamente.  
  
## <a name="example"></a>Ejemplo  
 Este error puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual C++ 2005: ya no es válido tener una `using` declaración a un tipo anidado; debe calificar explícitamente cada referencia realizada al tipo anidado, coloque el tipo en un nombre espacio o crear una definición de tipo.  
  
 El ejemplo siguiente genera C2885.  
  
```  
// C2885.cpp  
namespace MyNamespace {  
   class X1 {};  
}  
  
struct MyStruct {  
   struct X1 {  
      int i;  
   };  
};  
  
int main () {  
   using MyStruct::X1;   // C2885  
  
   // OK  
   using MyNamespace::X1;  
   X1 myX1;  
  
   MyStruct::X1 X12;  
  
   typedef MyStruct::X1 abc;  
   abc X13;  
   X13.i = 9;  
}  
```  
  
## <a name="example"></a>Ejemplo  
 Si usas el `using` palabra clave con un miembro de clase, C++ requiere que se defina el miembro dentro de otra clase (una clase derivada).  
  
 El ejemplo siguiente genera C2885.  
  
```  
// C2885_b.cpp  
// compile with: /c  
class A {  
public:  
   int i;  
};  
  
void z() {  
   using A::i;   // C2885 not in a class  
}  
  
class B : public A {  
public:  
   using A::i;  
};  
```