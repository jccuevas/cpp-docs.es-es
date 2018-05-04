---
title: Búsqueda de nombres dependiente de argumentos (Koenig) en las funciones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a06140522f9d4074eaa0403d0d05fe0f79adec0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="argument-dependent-name-koenig-lookup-on-functions"></a>Búsqueda de nombres dependientes de argumentos (Koenig) en las funciones
El compilador puede utilizar la búsqueda de nombres dependiente de argumentos para encontrar la definición de una llamada de función incompleta. La búsqueda de nombres dependiente de argumentos también se denomina búsqueda de Koenig. El tipo de cada argumento de una función se define dentro de una jerarquía de espacios de nombres, clases, estructuras, uniones o plantillas. Cuando se especifica una [postfijo](../cpp/postfix-expressions.md) llamada de función, el compilador busca la definición de función en la jerarquía asociada con cada tipo de argumento.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo, el compilador observa que la función `f()` toma un argumento `x`. El argumento `x` es de tipo `A::X`, que se define en el espacio de nombres `A`. El compilador busca el espacio de nombres `A` y encuentra una definición para la función `f()` que acepta un argumento de tipo `A::X`.  
  
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
