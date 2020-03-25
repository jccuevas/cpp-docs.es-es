---
title: Advertencia del compilador (nivel 4) C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: c27f16f7d2933ca1860b304afa6e04f96f0687f0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173912"
---
# <a name="compiler-warning-level-4-c4234"></a>Advertencia del compilador (nivel 4) C4234

se ha utilizado una extensión no estándar: la palabra clave ' keyword ' está reservada para uso futuro

El compilador no implementa todavía la palabra clave usada.

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, use [#pragma ADVERTENCIA](../../preprocessor/warning.md). Por ejemplo, para convertir C4234 en un problema de advertencia de nivel 4,

```cpp
#pragma warning(2:4234)
```

en el archivo de código fuente.
