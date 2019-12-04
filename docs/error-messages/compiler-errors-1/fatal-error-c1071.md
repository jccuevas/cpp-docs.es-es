---
title: Error irrecuperable C1071
ms.date: 11/04/2016
f1_keywords:
- C1071
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
ms.openlocfilehash: 2f39359d55b5564c6379c84f07e942cf3484e011
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747415"
---
# <a name="fatal-error-c1071"></a>Error irrecuperable C1071

no se esperaba el final de archivo encontrado en el comentario

El compilador llegó al final del archivo mientras analizaba un comentario.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Falta el terminador de comentario (*/).

1. Falta un carácter de nueva línea después de un Comentario en la última línea de un archivo de código fuente.

En el ejemplo siguiente se genera C1071:

```cpp
// C1071.cpp
int main() {
}

/* this comment is fine */
/* forgot the closing tag        // C1071
```
