---
title: Error grave de NMAKE U1070
ms.date: 11/04/2016
f1_keywords:
- U1070
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
ms.openlocfilehash: 35bea47f6626dfe283a537d3d96340921c37f3f6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484219"
---
# <a name="nmake-fatal-error-u1070"></a>Error grave de NMAKE U1070

ciclo en definición de macro 'nombredemacro'

La definición de macro dada contiene una macro cuya definición contiene la macro dada. Las definiciones de macro circulares no son válidas.

## <a name="example"></a>Ejemplo

Las siguientes definiciones de macro

```
ONE=$(TWO)
TWO=$(ONE)
```

Provoca el error siguiente:

```
cycle in macro definition 'TWO'
```