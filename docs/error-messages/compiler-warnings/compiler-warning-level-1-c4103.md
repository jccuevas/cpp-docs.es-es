---
title: ADVERTENCIA del compilador (nivel 1) C4103
ms.date: 11/04/2016
f1_keywords:
- C4103
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
ms.openlocfilehash: 456e7d393eb751e99c1969619ccfdcc649193c75
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627064"
---
# <a name="compiler-warning-level-1-c4103"></a>ADVERTENCIA del compilador (nivel 1) C4103

' FILENAME ': la alineación cambió después de incluir el encabezado, puede deberse a que falta el paquete de #pragma (pop)

El empaquetado afecta al diseño de las clases y, por lo general, si se empaquetan los cambios en los archivos de encabezado, puede haber problemas.

Use #pragma [Pack](../../preprocessor/pack.md)(pop) antes de salir del archivo de encabezado para resolver esta advertencia.

En el ejemplo siguiente se genera C4103:

```cpp
// C4103.h
#pragma pack(push, 4)

// defintions and declarations

// uncomment the following line to resolve
// #pragma pack(pop)
```

Y luego,

```cpp
// C4103.cpp
// compile with: /LD /W1
#include "c4103.h"   // C4103
```