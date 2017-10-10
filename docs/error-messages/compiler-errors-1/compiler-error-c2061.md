---
title: C2061 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2061
dev_langs:
- C++
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 82518c78b49418c10cc0cd07ae59e58336af08f3
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2061"></a>C2061 de Error del compilador
error de sintaxis: identificador 'identificador'  
  
 El compilador encontró un identificador donde no se esperaba. Asegúrese de que `identifier` se declara antes de utilizarla.  
  
 Un inicializador puede aparecer entre paréntesis. Para evitar este problema, escriba el declarador entre paréntesis o conviértalo en un `typedef`.  
  
 Este error también se produce cuando el compilador detecta una expresión como un argumento de plantilla de clase; usar [typename](../../cpp/typename.md) para indicar al compilador es un tipo.  
  
 El ejemplo siguiente genera C2061:  
  
```  
// C2061.cpp  
// compile with: /c  
template < A a >   // C2061  
// try the following line instead  
// template < typename b >  
class c{};  
```  
  
 C2061 puede aparecer si se pasa un nombre de instancia para [typeid](../../windows/typeid-cpp-component-extensions.md):  
  
```  
// C2061b.cpp  
// compile with: /clr  
ref struct G {  
   int i;  
};  
  
int main() {  
   G ^ pG = gcnew G;  
   System::Type ^ pType = typeid<pG>;   // C2061  
   System::Type ^ pType2 = typeid<G>;   // OK  
}  
```
