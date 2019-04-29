---
title: Error grave de NMAKE U1070
ms.date: 11/04/2016
f1_keywords:
- U1070
helpviewer_keywords:
- U1070
ms.assetid: 8639fc39-b4b1-48f5-ac91-0e9fb61680fd
ms.openlocfilehash: 35bea47f6626dfe283a537d3d96340921c37f3f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367244"
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