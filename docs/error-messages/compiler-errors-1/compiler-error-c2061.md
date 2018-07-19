---
title: C2061 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2061
dev_langs:
- C++
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d4d4b018dbab16e8e376a3331a85d0f1b1004f5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167384"
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