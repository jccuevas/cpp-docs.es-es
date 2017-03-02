---
title: Compilador advertencia (nivel 1) C4350 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4350
dev_langs:
- C++
helpviewer_keywords:
- C4350
ms.assetid: 4cc8ed67-64c4-4da5-a7a5-a639232baa23
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: c3a5411475d898562b8cba62ddeffcaf1dfec095
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4350"></a>Advertencia del compilador (nivel 1) C4350
cambio de comportamiento: se llamó a 'miembro1' en lugar de a 'miembro2'  
  
 No se puede enlazar un valor r a una referencia no const. En versiones anteriores de Visual C++, era posible enlazar un valor r a una referencia no const en una inicialización directa. Este código le proporciona una advertencia.  
  
 Por compatibilidad con versiones anteriores, todavía es posible enlazar valores r a referencias no const, pero son preferibles las conversiones estándar siempre que sea posible.  
  
 Esta advertencia representa un cambio de comportamiento del compilador de Visual C++ .NET 2002. Si está habilitada, esta advertencia podría haberse dado para código correcto. Por ejemplo, podría darse al utilizar el **std:: auto_ptr** plantilla de clase.  
  
 Si aparece esta advertencia, examine el código para ver si depende del enlace de valores r a referencias no const. Agregando una constante a la referencia o proporcionando una sobrecarga de referencia const adicional para solucionar el problema.  
  
 De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 El ejemplo siguiente genera C4350:  
  
```  
// C4350.cpp  
// compile with: /W1  
#pragma warning (default : 4350)  
class A {};  
  
class B  
{  
public:  
   B(B&){}  
   // try the following instead  
   // B(const B&){}  
  
   B(A){}  
   operator A(){ return A();}  
};  
  
B source() { return A(); }  
  
int main()  
{  
   B ap(source());   // C4350  
}  
```
