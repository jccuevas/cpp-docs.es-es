---
title: Error del compilador C3171 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3171
dev_langs:
- C++
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 32c58f2ecd9651c347f45c29139ffe0ed65a6e3b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46082266"
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