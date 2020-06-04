---
title: Búsqueda de nombres dependientes de argumentos (Koenig) en las funciones
ms.date: 11/04/2016
helpviewer_keywords:
- Koenig lookup
- argument-dependent lookup [C++]
ms.assetid: c0928401-da2c-4658-942d-9ba4df149c35
ms.openlocfilehash: 88811e8070fdfe398bc12734221dee772515d8bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190543"
---
# <a name="argument-dependent-name-koenig-lookup-on-functions"></a>Búsqueda de nombres dependientes de argumentos (Koenig) en las funciones

El compilador puede utilizar la búsqueda de nombres dependiente de argumentos para encontrar la definición de una llamada de función incompleta. La búsqueda de nombres dependiente de argumentos también se denomina búsqueda de Koenig. El tipo de cada argumento de una función se define dentro de una jerarquía de espacios de nombres, clases, estructuras, uniones o plantillas. Cuando se especifica una llamada a una función de [postfijo](../cpp/postfix-expressions.md) incompleta, el compilador busca la definición de función en la jerarquía asociada a cada tipo de argumento.

## <a name="example"></a>Ejemplo

En el ejemplo, el compilador observa que la función `f()` toma un argumento `x`. El argumento `x` es de tipo `A::X`, que se define en el espacio de nombres `A`. El compilador busca el espacio de nombres `A` y encuentra una definición para la función `f()` que acepta un argumento de tipo `A::X`.

```cpp
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
