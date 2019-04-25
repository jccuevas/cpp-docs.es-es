---
title: Error del compilador C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: 602c9ca1051646fca2c5788c036354047fad2522
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175444"
---
# <a name="compiler-error-c3171"></a>Error del compilador C3171

'module': no se puede especificar atributos module distintos en un proyecto

[módulo](../../windows/module-cpp.md) se encontraron atributos con listas de parámetros diferentes en dos de los archivos en una compilación. Solo uno único `module` atributo se puede especificar cada compilación.

Idéntico `module` atributos se pueden especificar más de un archivo de código fuente.

Por ejemplo, si la siguiente `module` se encontraron atributos:

```
// C3171.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];
int main() {}
```

Y luego,

```
// C3171b.cpp
// compile with: C3171.cpp
// C3171 expected
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];
```

el compilador generará el error C3171 (tenga en cuenta los valores de versión diferente).