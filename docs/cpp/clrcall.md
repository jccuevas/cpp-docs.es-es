---
title: "__clrcall | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__clrcall"
  - "__clrcall_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__clrcall (palabra clave) [C++]"
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
caps.latest.revision: 17
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __clrcall
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Especifica que solo se puede llamar a una función desde código administrado.  Utilice `__clrcall` para todas las funciones virtuales a las que solo se llamará desde código administrado.  Sin embargo esta convención de llamada no se puede utilizar para las funciones a las que llamará desde código nativo.  
  
 Utilice `__clrcall` para mejorar el rendimiento cuando se llame desde una función administrada a una función administrada virtual o desde una función administrada a una función administrada mediante puntero.  
  
 Los puntos de entrada son funciones independientes generadas por el compilador.  Si una función tiene puntos de entrada nativos y administrados, uno de ellos será la función real con la implementación de la función.  La otra función será una función independiente \(un código thunk\) que llama a la función real y deja que Common Language Runtime realice PInvoke.  Cuando se marca una función como `__clrcall`, se indica que la implementación de la función debe ser MSIL y que la función de punto de entrada nativo no se generará.  
  
 Cuando se toma la dirección de una función nativa si no se especifica `__clrcall`, el compilador usa el punto de entrada nativo.  `__clrcall` indica que la función es una función administrada y no es necesario realizar la transición de administrada a nativa.  En ese caso, el compilador usa el punto de entrada administrado.  
  
 Cuando se usa **\/clr** \(no **\/clr:pure** ni **\/clr:safe**\) y no se usa `__clrcall`, la aceptación de la dirección de una función siempre devuelve la dirección de la función de punto de entrada nativo.  Cuando se utiliza `__clrcall`, la función de punto de entrada nativo no se crea, por lo que se obtiene la dirección de la función administrada, no una función de código thunk de punto de entrada.  Para obtener más información, vea [Doble thunk](../dotnet/double-thunking-cpp.md).  
  
 [\/clr \(Compilación de Common Language Runtime\)](../build/reference/clr-common-language-runtime-compilation.md) implica que todas las funciones y punteros de función son `__clrcall` y el compilador no permitirá que una función dentro del compilando esté marcada como algo que no sea `__clrcall`.  Cuando se utiliza **\/clr:pure**, `__clrcall` solo se puede especificar en punteros de función y en declaraciones externas.  
  
 Se puede llamar directamente a funciones `__clrcall` desde código de C\+\+ existente que se compiló usando **\/clr** siempre que esa función tenga una implementación MSIL.  No se puede llamar a funciones `__clrcall` directamente desde funciones con asm insertado y funciones intrínsecas de CPU, por ejemplo, incluso si esas funciones se compilan con **\/clr**.  
  
 Los punteros de función`__clrcall` solo están diseñados para usarse en el dominio de aplicación en el que se crearon.  En lugar de pasar punteros de función `__clrcall` a través de dominios de aplicación, utilice <xref:System.CrossAppDomainDelegate>.  Para obtener más información, vea [Dominios de aplicación y Visual C\+\+](../dotnet/application-domains-and-visual-cpp.md).  
  
## Ejemplo  
  
```  
// clrcall.cpp  
// compile with: /clr:oldSyntax /LD  
void __clrcall Test1( ) {}  
void (__clrcall *fpTest1)( ) = &Test1;  
```  
  
## Ejemplo  
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
  
  **en Func1**  
**&¡Func1\! \= pf, la comparación sufre un error**  
**en Func1**  
**en Func1**   
## Ejemplo  
 En el ejemplo siguiente se muestra que se puede definir un puntero de función, de modo que se declare que el puntero de función solo se invoque desde código administrado.  Esto permite que el compilador llame directamente a la función administrada y evite el punto de entrada nativo \(problema de doble código thunk\).  
  
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
  
## Vea también  
 [Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)