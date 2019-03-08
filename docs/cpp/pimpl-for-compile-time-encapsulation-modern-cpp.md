---
title: Pimpl para encapsulación en tiempo de compilación (C++ moderno)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
ms.openlocfilehash: 6e114e2802dd4b2e5d1497867e2224be90c4752d
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220691"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>Pimpl para encapsulación en tiempo de compilación (C++ moderno)

El *pimpl modismo* es una técnica de C++ moderna para ocultar la implementación, para minimizar el acoplamiento y separar las interfaces. Pimpl es la abreviatura de "puntero a la implementación." Ya puede estar familiarizado con el concepto pero sabe otros nombres como expresión sonrisa Cat o Firewall del compilador.

## <a name="why-use-pimpl"></a>¿Por qué usar pimpl?

Le mostramos cómo la expresión pimpl puede mejorar el ciclo de vida de desarrollo de software:

- Minimización de dependencias de compilación.

- Separación de la interfaz y la implementación.

- Portabilidad de.

## <a name="pimpl-header"></a>Encabezado Pimpl

```cpp
// my_class.h
class my_class {
   //  ... all public and protected stuff goes here ...
private:
   class impl; unique_ptr<impl> pimpl; // opaque type here
};
```

La expresión pimpl evita la recompilación cascadas y diseños de objeto frágil. También es adecuado para los tipos conocidos (de manera transitiva).

## <a name="pimpl-implementation"></a>Implementación de Pimpl

Definir la `impl` clase en el archivo. cpp.

```cpp
// my_class.cpp
class my_class::impl {  // defined privately here
  // ... all private data and functions: all of these
  //     can now change without recompiling callers ...
};
my_class::my_class(): pimpl( new impl )
{
  // ... set impl values ...
}
```

## <a name="best-practices"></a>Procedimientos recomendados

Considere la posibilidad de agregar compatibilidad para la especialización de intercambio no producen excepciones.

## <a name="see-also"></a>Vea también

[Aquí está otra vez C++ (C++ moderno)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
