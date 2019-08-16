---
title: Advertencia del compilador (nivel 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: 80ad388b26b2b972aa1301c1f335d0361a75f15f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401051"
---
# <a name="compiler-warning-level-4-c4235"></a>Advertencia del compilador (nivel 4) C4235

se ha utilizado una extensión no estándar : la palabra clave 'palabra clave' no se admite en esta arquitectura

El compilador aún no admite la palabra clave utilizada.

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, use [advertencia #pragma](../../preprocessor/warning.md). Por ejemplo, para convertir C4235 en una advertencia de nivel 2, utilice la siguiente línea de código

```
#pragma warning(2:4235)
```

en el archivo de código fuente.