---
title: ADVERTENCIA del compilador (nivel 1) C4218
ms.date: 11/04/2016
f1_keywords:
- C4218
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
ms.openlocfilehash: f1db3eabc3b614019676dc4494e83104c62fe579
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627306"
---
# <a name="compiler-warning-level-1-c4218"></a>ADVERTENCIA del compilador (nivel 1) C4218

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