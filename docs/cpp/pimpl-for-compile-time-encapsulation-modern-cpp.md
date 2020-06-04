---
title: Pimpl para encapsulación en tiempo de compilación (C++ moderno)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
ms.openlocfilehash: f1eb06ad3a52be486f085babf699677951b1ee71
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245173"
---
# <a name="pimpl-for-compile-time-encapsulation-modern-c"></a>Pimpl para encapsulación en tiempo de compilación (C++ moderno)

La *expresión pimpl* es una técnica C++ moderna para ocultar la implementación, para minimizar el acoplamiento y para separar las interfaces. Pimpl es la abreviatura de "puntero a implementación". Es posible que ya esté familiarizado con el concepto, pero lo sepa con otros nombres como Cheshire cat o la expresión de firewall del compilador.

## <a name="why-use-pimpl"></a>¿Por qué usar pimpl?

A continuación se muestra cómo la expresión pimpl puede mejorar el ciclo de vida de desarrollo de software:

- Minimización de las dependencias de compilación.

- Separación de la interfaz y la implementación.

- Portabilidad.

## <a name="pimpl-header"></a>Encabezado Pimpl

```cpp
// my_class.h
class my_class {
   //  ... all public and protected stuff goes here ...
private:
   class impl; unique_ptr<impl> pimpl; // opaque type here
};
```

La expresión pimpl evita la recompilación en cascada y los diseños de objeto frágiles. Es adecuado para los tipos populares (transitivamente).

## <a name="pimpl-implementation"></a>Implementación de Pimpl

Defina la clase `impl` en el archivo. cpp.

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

Considere la posibilidad de agregar compatibilidad para la especialización de intercambio que no inicia.

## <a name="see-also"></a>Vea también

[Bienvenido de nuevo aC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
