---
title: Pimpl para encapsulación en tiempo de compilación (C++ moderno) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c3e8a90a-b328-4990-82bb-e1b147f76e07
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 83b01a58745185499ac02a254a207fac2779be26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059009"
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

[Aquí está otra vez C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)