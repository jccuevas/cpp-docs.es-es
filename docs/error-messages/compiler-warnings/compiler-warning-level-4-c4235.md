---
title: Advertencia del compilador (nivel 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: 80ad388b26b2b972aa1301c1f335d0361a75f15f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559852"
---
# <a name="compiler-warning-level-4-c4235"></a>Advertencia del compilador (nivel 4) C4235

se ha utilizado una extensión no estándar : la palabra clave 'palabra clave' no se admite en esta arquitectura

El compilador aún no admite la palabra clave utilizada.

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, use [advertencia #pragma](../../preprocessor/warning.md). Por ejemplo, para convertir C4235 en una advertencia de nivel 2, utilice la siguiente línea de código

```
#pragma warning(2:4235)
```

en el archivo de código fuente.