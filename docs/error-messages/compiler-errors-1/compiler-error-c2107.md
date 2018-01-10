---
title: Error del compilador C2107 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2107
dev_langs: C++
helpviewer_keywords: C2107
ms.assetid: 2866a121-884e-4bb5-8613-36de5817000e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6123da392cc6437593b0805c5bc6e94f450e282
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2107"></a>Error del compilador C2107
índice no válido, direccionamiento indirecto no permitido  
  
 Se ha intentado aplicar un subíndice a una expresión que no se evalúa como puntero.  
  
## <a name="example"></a>Ejemplo  
 El error C2107 puede aparecer si utiliza incorrectamente el puntero `this` de un tipo de valor para tener acceso al indizador predeterminado del tipo. Para obtener más información, consulte [semántica de este puntero](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer).  
  
 El ejemplo siguiente genera el error C2107.  
  
```  
// C2107.cpp  
// compile with: /clr  
using namespace System;  
  
value struct B {  
   property String ^ default[String ^] {  
      String ^ get(String ^ data) {  
         return "abc";  
      }  
   }  
   void Test() {  
      Console::WriteLine("{0}", this["aa"]);   // C2107  
      Console::WriteLine("{0}", this->default["aa"]);   // OK  
   }  
};  
  
int main() {  
   B ^ myb = gcnew B();  
   myb->Test();  
}  
```