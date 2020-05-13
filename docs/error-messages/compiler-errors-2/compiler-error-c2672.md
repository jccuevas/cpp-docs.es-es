---
title: Error del compilador C2672
ms.date: 10/24/2017
f1_keywords:
- C2672
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
ms.openlocfilehash: 9f844b54285a7df69bfb4387a7afcc82dfef9252
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177136"
---
# <a name="compiler-error-c2672"></a>Error del compilador C2672

> '*función*': no se encontró ninguna función sobrecargada coincidente

El compilador no encontró una función sobrecargada que coincida con la función especificada. No se encontró ninguna función que acepte parámetros coincidentes o que ninguna función coincidente tenga la accesibilidad necesaria en el contexto.

Cuando se usan en determinados algoritmos o contenedores de la biblioteca estándar, los tipos deben proporcionar miembros accesibles o funciones Friend que cumplan los requisitos del contenedor o el algoritmo. Por ejemplo, los tipos de iterador deberían derivar de `std::iterator<>`. Las operaciones de comparación o el uso de otros operadores en tipos de elementos de contenedor pueden requerir que el tipo se considere como un operando a la izquierda y a la derecha. El uso del tipo como un operando a la derecha puede requerir la implementación del operador como una función no miembro del tipo.

## <a name="example"></a>Ejemplo

Las versiones del compilador anteriores a Visual Studio 2017 no realizaron la comprobación de acceso en nombres completos en algunos contextos de plantilla. Esto puede interferir con el comportamiento esperado de SFINAE, ya que se espera un error en la sustitución debido a la inaccesibilidad de un nombre. Esto podría haber provocado un bloqueo o un comportamiento inesperado en tiempo de ejecución, ya que el compilador hubiera llamado incorrectamente a la sobrecarga incorrecta del operador. En Visual Studio 2017, se genera un error del compilador.

Este ejemplo se compila en Visual Studio 2015, pero genera un error en Visual Studio 2017. Para corregir este problema, haga que el miembro de parámetro de plantilla sea accesible donde se evalúa.

```cpp
#include <type_traits>

template <class T> class S {
// public:    // Uncomment this line to fix
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x)
{
    return (x == 0);
}

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```
