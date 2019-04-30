---
title: Error del compilador C2672
ms.date: 10/24/2017
f1_keywords:
- C2672
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
ms.openlocfilehash: df0f656c9db23739ec62629088b9cc5f7950a92d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386868"
---
# <a name="compiler-error-c2672"></a>Error del compilador C2672

> '*función*': no hay coincidencia sobrecargados se encuentra la función

El compilador no pudo encontrar una función sobrecargada que coincida con la función especificada. Se ha encontrado ninguna función que toma parámetros o ninguna función de búsqueda de coincidencias de coincidencia tiene la accesibilidad necesaria en contexto.

Cuando se utiliza por determinados algoritmos o contenedores de la biblioteca estándar, deben proporcionar los tipos de miembros accesibles o funciones friend que cumplen los requisitos del contenedor o el algoritmo. Por ejemplo, los tipos de iterador deben derivar de `std::iterator<>`. Las operaciones de comparación o el uso de otros operadores en tipos de elemento contenedor puede requerir el tipo se considera como un izquierdo y un operando de la derecha. Uso del tipo como un operando derecho puede requerir la implementación del operador como una función que no es miembro del tipo.

## <a name="example"></a>Ejemplo

Versiones del compilador antes de Visual Studio 2017 no se ha realizado la comprobación de acceso en nombres completos en algunos contextos de plantilla. Esto puede interferir con el comportamiento esperado de SFINAE, ya que se espera un error en la sustitución debido a la inaccesibilidad de un nombre. Esto podría haber provocado un bloqueo o un comportamiento inesperado en tiempo de ejecución, ya que el compilador hubiera llamado incorrectamente a la sobrecarga incorrecta del operador. En Visual Studio 2017, se genera un error del compilador.

En este ejemplo se compila en Visual Studio 2015, pero se genera un error en Visual Studio 2017. Para corregir este problema, hacer que el miembro de parámetro de plantilla accesible en el se evalúa.

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