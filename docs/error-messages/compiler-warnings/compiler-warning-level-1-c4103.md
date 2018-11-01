---
title: Compilador advertencia (nivel 1) C4103
ms.date: 11/04/2016
f1_keywords:
- C4103
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
ms.openlocfilehash: 15d7403d461467e33b7e89957821a311179d33a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577819"
---
# <a name="compiler-warning-level-1-c4103"></a>Compilador advertencia (nivel 1) C4103

'filename': ha cambiado después de incluir el encabezado, la alineación puede ser debido a que faltan #pragma Pack (POP)

Empaquetado afecta al diseño de clases y, normalmente, si el empaquetado cambia a través de los archivos de encabezado, puede haber problemas.

Utilice #pragma [pack](../../preprocessor/pack.md)(pop) antes de salir el archivo de encabezado para resolver esta advertencia.

El ejemplo siguiente genera C4103:

```
// C4103.h
#pragma pack(push, 4)

// defintions and declarations

// uncomment the following line to resolve
// #pragma pack(pop)
```

Y luego,

```
// C4103.cpp
// compile with: /LD /W1
#include "c4103.h"   // C4103
```