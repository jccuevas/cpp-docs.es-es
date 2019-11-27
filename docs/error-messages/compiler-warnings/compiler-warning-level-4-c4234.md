---
title: Advertencia del compilador (nivel 4) C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: 63a22fed0832677837eb786268fc92946d295b79
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541775"
---
# <a name="compiler-warning-level-4-c4234"></a>Advertencia del compilador (nivel 4) C4234

se ha utilizado una extensión no estándar: la palabra clave ' keyword ' está reservada para uso futuro

El compilador no implementa todavía la palabra clave usada.

Esta advertencia suele convertirse automáticamente en un error. Si desea modificar este comportamiento, use [#pragma ADVERTENCIA](../../preprocessor/warning.md). Por ejemplo, para convertir C4234 en un problema de advertencia de nivel 4,

```cpp
#pragma warning(2:4234)
```

en el archivo de código fuente.