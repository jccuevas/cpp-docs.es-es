---
title: Error del compilador C3170 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3170
dev_langs:
- C++
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7a193abcd59c3e9454eec1108f1e3bbb66efcc8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070371"
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