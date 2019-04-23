---
title: Advertencia del compilador (nivel 4) C4211
ms.date: 11/04/2016
f1_keywords:
- C4211
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
ms.openlocfilehash: 6d61191c4a7ed950d979158ccdfa3a390439b019
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59778311"
---
# <a name="compiler-warning-level-4-c4211"></a>Advertencia del compilador (nivel 4) C4211

extensión no estándar utilizada: redefinido extern como estática

Con las extensiones de Microsoft (/Ze) de forma predeterminada, se puede redefinir un `extern` identificador como **estático**.

## <a name="example"></a>Ejemplo

```
// C4211.c
// compile with: /W4
extern int i;
static int i;   // C4211

int main()
{
}
```

Dichas redefiniciones no son válidas en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).
