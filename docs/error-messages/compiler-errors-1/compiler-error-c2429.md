---
title: Error del compilador C2429
ms.date: 11/16/2017
f1_keywords:
- C2429
helpviewer_keywords:
- C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
ms.openlocfilehash: a5d1e98e91c541729a93f731eede9b047589c63a
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447988"
---
# <a name="compiler-error-c2429"></a>Error del compilador C2429

> '*característica del lenguaje*'requiere la marca de compilador'*opción del compilador*'

La característica de lenguaje requiere una opción de compilador específica para obtener soporte técnico.

El error **C2429: característica del lenguaje 'anidado de namespace-definition' requiere la marca de compilador ' / std: c ++ 17"** se genera si se intenta definir una *espacio de nombres compuesto*, un espacio de nombres que contiene uno o más nombres de espacio de nombres con ámbito anidado, a partir de Visual Studio 2015 Update 5. (En Visual Studio 2017 versión 15.3, el **/std: c ++ más reciente** modificador es necesario.) Compuesta de espacio de nombres no se permiten definiciones en C++ antes de C ++ 17. El compilador admite las definiciones de espacio de nombres compuestos cuando el [/std: c ++ 17](../../build/reference/std-specify-language-standard-version.md) se especificó la opción del compilador:

```cpp
// C2429a.cpp
namespace a::b { int i; } // C2429 starting in Visual Studio 2015 Update 3.
                          // Use /std:c++17 to fix, or do this:
// namespace a { namespace b { int i; }}

int main() {
   a::b::i = 2;
}
```
