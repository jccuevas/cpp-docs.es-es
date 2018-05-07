---
title: C2429 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/16/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2429
dev_langs:
- C++
helpviewer_keywords:
- C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 032df433b28e83f720fe76952a541b59bda889f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2429"></a>C2429 de Error del compilador

> '*característica de lenguaje*'requiere la marca de compilador'*opción del compilador*'

La característica de lenguaje requiere una opción del compilador específico para soporte técnico.

El error **C2429: característica de lenguaje 'anidado de espacio de nombres-definición' requiere la marca de compilador ' / std:c ++ 17'** se genera si se intenta definir una *espacio de nombres compuesto*, un espacio de nombres que contiene uno o más ámbito anidado espacios de nombres, a partir de Visual Studio 2015 Update 5. (En Visual Studio 2017 versión 15.3, el **/std:c ++ más reciente** conmutador es necesario.) Compuesta espacio de nombres no se permiten definiciones en C++ antes de C ++ 17. El compilador admite las definiciones de espacio de nombres compuestos cuando el [/std:c ++ 17](../../build/reference/std-specify-language-standard-version.md) se especifica la opción del compilador:

```cpp
// C2429a.cpp
namespace a::b { int i; } // C2429 starting in Visual C++ 2015 Update 3.
                          // Use /std:c++17 to fix, or do this:
// namespace a { namespace b { int i; }}

int main() {
   a::b::i = 2;
}
```
