---
title: Error del compilador C3170
ms.date: 11/04/2016
f1_keywords:
- C3170
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
ms.openlocfilehash: e2d74a637e2902fcf636b49068882f32aa706f94
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761769"
---
# <a name="compiler-error-c3170"></a>Error del compilador C3170

no se pueden tener identificadores de módulo diferentes en un proyecto

se encontraron atributos de [módulo](../../windows/module-cpp.md) con nombres diferentes en dos de los archivos de una compilación. Solo se puede especificar un atributo de `module` único por compilación.

Se pueden especificar atributos idénticos `module` en más de un archivo de código fuente.

Por ejemplo, si se encuentran los siguientes atributos de módulo:

```cpp
// C3170.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
int main() {}
```

Y luego,

```cpp
// C3170b.cpp
// compile with: C3170.cpp
// C3170 expected
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
```

el compilador generaría C3170 (tenga en cuenta los nombres diferentes).
