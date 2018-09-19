---
title: Error irrecuperable C1071 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1071
dev_langs:
- C++
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b4487de60148e1da7668bc44c996c5dfb955a9d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033009"
---
# <a name="fatal-error-c1071"></a>Error irrecuperable C1071

no se esperaba el final de archivo encontrado en el comentario

El compilador ha alcanzado el final del archivo mientras se analizaba un comentario.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Falta el terminador de comentario (* /).

1. Falta el carácter de nueva línea después de un comentario en la última línea de un archivo de origen.

El ejemplo siguiente genera C1071:

```
// C1071.cpp
int main() {
}

/* this comment is fine */
/* forgot the closing tag        // C1071
```