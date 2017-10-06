---
title: __clrcall | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __clrcall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 10e0835064298306c4fa53d4d15f59ecc6c73217
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="clrcall"></a>__clrcall
**Específicos de Microsoft**  
  
 Especifica que solo se puede llamar a una función desde código administrado.  Utilice `__clrcall` para todas las funciones virtuales a las que solo se llamará desde código administrado. Sin embargo esta convención de llamada no se puede utilizar para las funciones a las que llamará desde código nativo.  
  
 Utilice `__clrcall` para mejorar el rendimiento cuando se llame desde una función administrada a una función administrada virtual o desde una función administrada a una función administrada mediante puntero.  
  
 Los puntos de entrada son funciones independientes generadas por el compilador. Si una función tiene puntos de entrada nativos y administrados, uno de ellos será la función real con la implementación de la función. La otra función será una función independiente (un código thunk) que llama a la función real y deja que Common Language Runtime realice PInvoke. Cuando se marca una función como `__clrcall`, se indica que la implementación de la función debe ser MSIL y que la función de punto de entrada nativo no se generará.  
  
 Cuando se toma la dirección de una función nativa si no se especifica `__clrcall`, el compilador usa el punto de entrada nativo. `__clrcall` indica que la función es una función administrada y no es necesario realizar la transición de administrada a nativa. En ese caso, el compilador usa el punto de entrada administrado.  
  
 Cuando **/CLR** (no **/CLR: pure** o **/CLR: safe**) se usa y `__clrcall` no es utilizada, tomar la dirección de una función siempre devuelve la dirección de entrada nativo función de punto. Cuando se utiliza `__clrcall`, la función de punto de entrada nativo no se crea, por lo que se obtiene la dirección de la función administrada, no una función de código thunk de punto de entrada. Para obtener más información, consulte [doble thunk](../dotnet/double-thunking-cpp.md). Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015.  
  
 [/CLR (compilación de common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) implica que todas las funciones y los punteros de función son `__clrcall` y el compilador no permite que una función dentro de la operación de compilación se marquen como algo distinto de `__clrcall`. Cuando **/CLR: pure** se utiliza, `__clrcall` sólo se puede especificar en punteros de función y declaraciones externas.  
  
 Se puede llamar directamente a `__clrcall` funciones desde código C++ existente que se ha compilado con **/CLR** siempre que esa función tenga una implementación MSIL. `__clrcall`las funciones no se puede llamar directamente desde funciones con asm insertado y denomínelo intrínsecas de CPU, por ejemplo, incluso si esas funciones se compilan con **/CLR**.  
  
 Los punteros de función`__clrcall` solo están diseñados para usarse en el dominio de aplicación en el que se crearon.  En lugar de pasar punteros de función `__clrcall` a través de dominios de aplicación, utilice <xref:System.CrossAppDomainDelegate>. Para obtener más información, consulte [dominios de aplicación y Visual C++](../dotnet/application-domains-and-visual-cpp.md).  
  
## <a name="example"></a>Ejemplo  
 Observe que cuando una función se declare con `__clrcall`, el código se generará cuando sea necesario; por ejemplo, cuando se llame a la función.  
  
```  
// clrcall2.cpp  
// compile with: /clr  
using namespace System;  
int __clrcall Func1() {  
   Console::WriteLine("in Func1");  
   return 0;  
}  
  
// Func1 hasn't been used at this point (code has not been generated),   
// so runtime returns the adddress of a stub to the function  
int (__clrcall *pf)() = &Func1;  
  
// code calls the function, code generated at difference address  
int i = pf();   // comment this line and comparison will pass  
  
int main() {  
   if (&Func1 == pf)  
      Console::WriteLine("&Func1 == pf, comparison succeeds");  
   else   
      Console::WriteLine("&Func1 != pf, comparison fails");  
  
   // even though comparison fails, stub and function call are correct  
   pf();  
   Func1();  
}  
```  
  
```Output  
in Func1  
&Func1 != pf, comparison fails  
in Func1  
in Func1  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra que se puede definir un puntero de función, de modo que se declare que el puntero de función solo se invoque desde código administrado. Esto permite que el compilador llame directamente a la función administrada y evite el punto de entrada nativo (problema de doble código thunk).  
  
```  
// clrcall3.cpp  
// compile with: /clr  
void Test() {  
   System::Console::WriteLine("in Test");  
}  
  
int main() {  
   void (*pTest)() = &Test;  
   (*pTest)();  
  
   void (__clrcall *pTest2)() = &Test;  
   (*pTest2)();  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)   
 [Palabras clave](../cpp/keywords-cpp.md)
