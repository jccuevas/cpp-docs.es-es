---
title: C2672 de Error del compilador | Documentos de Microsoft
ms.date: 10/24/2017
ms.technology:
- cpp-tools
ms.topic: error-reference
f1_keywords:
- C2672
dev_langs:
- C++
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52663aed470aff254d07cba6a65f484269d8703d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2672"></a>C2672 de Error del compilador

> '*función*': ninguna sobrecarga ha encontrado una función

El compilador no pudo encontrar una función sobrecargada que coincida con la función especificada. No se encontró ninguna función que toma parámetros o ninguna función de búsqueda de coincidencias de búsqueda de coincidencias tiene la accesibilidad necesaria en contexto.

Cuando se utiliza por determinados algoritmos o contenedores de la biblioteca estándar, deben proporcionar sus tipos de los miembros accesibles o funciones de confianza que cumplen los requisitos del contenedor o el algoritmo. Por ejemplo, los tipos de iterador deben derivarse de `std::iterator<>`. Las operaciones de comparación o el uso de otros operadores en tipos de elemento de contenedor puede requerir el tipo se considera como un izquierdo y un operando derecho. El uso de tipo como un operando derecho puede requerir la implementación del operador como una función no es miembro del tipo.

## <a name="example"></a>Ejemplo

Las versiones del compilador antes de 2017 de Visual Studio no realizó la comprobación de nombres completos en algunos contextos de plantilla de acceso. Esto puede interferir con el comportamiento esperado de SFINAE, ya que se espera un error en la sustitución debido a la inaccesibilidad de un nombre. Esto podría haber provocado un bloqueo o un comportamiento inesperado en tiempo de ejecución, ya que el compilador hubiera llamado incorrectamente a la sobrecarga incorrecta del operador. En Visual Studio 2017, se genera un error del compilador.

En este ejemplo se compila en Visual Studio 2015, pero se produce un error en Visual Studio de 2017. Para corregir este problema, realice el miembro de parámetro de plantilla accesible donde se evalúa.

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