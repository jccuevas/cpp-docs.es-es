---
title: "B&#250;squeda de nombres dependientes de argumentos (Koenig) en las funciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "búsqueda dependiente de argumentos [C++]"
  - "Koenig (búsqueda)"
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# B&#250;squeda de nombres dependientes de argumentos (Koenig) en las funciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El compilador puede utilizar la búsqueda de nombres dependiente de argumentos para encontrar la definición de una llamada de función incompleta.  La búsqueda de nombres dependiente de argumentos también se denomina búsqueda de Koenig.  El tipo de cada argumento de una función se define dentro de una jerarquía de espacios de nombres, clases, estructuras, uniones o plantillas.  Cuando se especifica una llamada de función [postfija](../cpp/postfix-expressions.md) incompleta, el compilador busca la definición de función en la jerarquía asociada a cada tipo de argumento.  
  
## Ejemplo  
 En el ejemplo, el compilador observa que la función `f()` toma un argumento `x`.  El argumento `x` es de tipo `A::X`, que se define en el espacio de nombres `A`.  El compilador busca el espacio de nombres `A` y encuentra una definición para la función `f()` que acepta un argumento de tipo `A::X`.  
  
```  
// argument_dependent_name_koenig_lookup_on_functions.cpp  
namespace A  
{  
   struct X  
   {  
   };  
   void f(const X&)  
   {  
   }  
}  
int main()  
{  
// The compiler finds A::f() in namespace A, which is where   
// the type of argument x is defined. The type of x is A::X.  
   A::X x;  
   f(x);     
}  
```  
  
## Vea también  
 [Conformidad del compilador mejorado de Visual C\+\+ .NET 2003](../misc/visual-cpp-dotnet-2003-enhanced-compiler-conformance.md)