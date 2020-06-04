---
title: Error del compilador C3171
ms.date: 11/04/2016
f1_keywords:
- C3171
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
ms.openlocfilehash: a3af19fa6b4f4def9bb42325f648109cfafcdaef
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761756"
---
# <a name="compiler-error-c3171"></a>Error del compilador C3171

' module ': no se pueden especificar atributos de módulo diferentes en un proyecto

se encontraron atributos de [módulo](../../windows/module-cpp.md) con diferentes listas de parámetros en dos de los archivos de una compilación. Solo se puede especificar un atributo de `module` único por compilación.

Se pueden especificar atributos idénticos `module` en más de un archivo de código fuente.

Por ejemplo, si se encuentran los siguientes atributos de `module`:

```cpp
// C3171.cpp
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];
int main() {}
```

Y luego,

```cpp
// C3171b.cpp
// compile with: C3171.cpp
// C3171 expected
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];
```

el compilador generaría C3171 (tenga en cuenta los diferentes valores de versión).
