---
title: Error del compilador C2955 | Documentos de Microsoft
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2955
dev_langs:
- C++
helpviewer_keywords:
- C2955
ms.assetid: 77709fb6-d69b-46fd-a62f-e8564563d01b
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: b790beb88de009e1c7161f3c9af6b3e21c22fd8e
ms.openlocfilehash: 1d2d589ad29896cda2657888c616388e50cc397a
ms.lasthandoff: 03/29/2017

---
# <a name="compiler-error-c2955"></a>Error del compilador C2955
'identificador': el uso de la plantilla de clase o el alias genérico requiere una lista de plantillas o de argumentos genéricos  
  
 No puede usar una plantilla de clase o de clase genérica como identificador sin una lista de plantillas o de argumentos genéricos.  
  
 Para obtener más información, consulte [plantillas de clase](../../cpp/class-templates.md).  
  
 El ejemplo siguiente genera el error C2955 y muestra cómo corregirlo.  
  
```  
// C2955.cpp  
// compile with: /c  
template<class T>   
class X {};  
  
X x1;   // C2955  
X<int> x2;   // OK - this is how to fix it.  
```  
  
 El error C2955 también se puede producir al intentar efectuar una definición fuera de línea para una función declarada en una plantilla de clase:  
  
```  
// C2955_b.cpp  
// compile with: /c  
template <class T>  
class CT {  
public:  
   void CTFunc();  
   void CTFunc2();  
};  
  
void CT::CTFunc() {}   // C2955  
  
// OK - this is how to fix it  
template <class T>  
void CT<T>::CTFunc2() {}  
  
```  
  
 También se puede producir el error C2955 al usar genéricos:  
  
```  
// C2955_c.cpp  
// compile with: /clr  
generic <class T>   
ref struct GC {   
   T t;  
};  
  
int main() {  
   GC^ g;   // C2955  
   GC <int>^ g;  
}  
```

## <a name="example"></a>Ejemplo
**Visual Studio 2017 y versiones posterior:** el compilador diagnostica correctamente las listas de argumentos de plantilla que faltan cuando la plantilla aparece en una lista de parámetros de plantilla (por ejemplo, como parte de un argumento de plantilla predeterminado o un parámetro de plantilla sin tipo). El siguiente código se compila en Visual Studio 2015, pero genera un error en Visual Studio 2017.

```
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias 
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

