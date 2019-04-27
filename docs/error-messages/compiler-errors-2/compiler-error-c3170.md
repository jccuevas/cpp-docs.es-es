---
title: Error del compilador C3170
ms.date: 11/04/2016
f1_keywords:
- C3170
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
ms.openlocfilehash: 5ef39e4580601dd90b5695d9115902bb5b834409
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174710"
---
# <a name="compiler-error-c3170"></a>Error del compilador C3170

no puede tener identificadores de módulo distintos en un proyecto

[módulo](../../windows/module-cpp.md) se encontraron atributos con nombres diferentes en dos de los archivos en una compilación. Solo uno único `module` atributo se puede especificar cada compilación.

Idéntico `module` atributos se pueden especificar más de un archivo de código fuente.

Por ejemplo, si se encontraron los siguientes atributos de módulo:

```
// C3170.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
int main() {}
```

Y luego,

```
// C3170b.cpp
// compile with: C3170.cpp
// C3170 expected
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];
```

el compilador generará el error C3170 (tenga en cuenta los nombres diferentes).