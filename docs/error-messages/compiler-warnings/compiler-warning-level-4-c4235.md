---
title: Advertencia del compilador (nivel 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: df80bec2294929be463425d74d4bf00421b368e6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198437"
---
# <a name="compiler-warning-level-4-c4235"></a>Advertencia del compilador (nivel 4) C4235

se ha utilizado una extensión no estándar : la palabra clave 'palabra clave' no se admite en esta arquitectura

El compilador aún no admite la palabra clave utilizada.

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, use [#pragma ADVERTENCIA](../../preprocessor/warning.md). Por ejemplo, para convertir C4235 en una advertencia de nivel 2, utilice la siguiente línea de código

```cpp
#pragma warning(2:4235)
```

en el archivo de código fuente.
