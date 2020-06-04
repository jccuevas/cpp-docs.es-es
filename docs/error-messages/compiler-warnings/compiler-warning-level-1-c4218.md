---
title: Advertencia del compilador (nivel 1) C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: f7553b30a17f50f559351353552fd656fceb8657
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199802"
---
# <a name="compiler-warning-level-1-c4218"></a>Advertencia del compilador (nivel 1) C4218

se ha utilizado una extensión no estándar: debe especificar al menos una clase de almacenamiento o un tipo.

Con las extensiones de Microsoft (/ZE) predeterminadas, puede declarar una variable sin especificar un tipo o una clase de almacenamiento. El tipo predeterminado es `int`.

## <a name="example"></a>Ejemplo

```cpp
// C4218.c
// compile with: /W4
i;  // C4218

int main()
{
}
```

Estas declaraciones no son válidas con compatibilidad con ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
