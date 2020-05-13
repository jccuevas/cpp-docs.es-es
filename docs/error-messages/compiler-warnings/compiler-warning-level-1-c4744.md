---
title: Advertencia del compilador (nivel 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: f932b1bcdf011678d4f85e0edf1e116a954b59fe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367378"
---
# <a name="compiler-warning-level-1-c4744"></a>Advertencia del compilador (nivel 1) C4744

'var' tiene diferentes tipos en 'file1' y 'file2': 'type1' y 'type2'

Una variable externa a la que se hace referencia o se define en dos archivos tiene tipos diferentes en esos archivos.  Para resolverlo, haga que las definiciones de tipo sean las mismas o cambie el nombre de la variable en uno de los archivos.

C4744 se emite solo cuando los archivos se compilan con /GL.  Para obtener más información, consulte [/GL (Optimización de todo el programa)](../../build/reference/gl-whole-program-optimization.md).

> [!NOTE]
> C4744 suele producirse en archivos C (no C++), porque en C++ un nombre de variable se decora con información de tipo.  Cuando el ejemplo (abajo) se compila como C++, obtendrá el error del vinculador LNK2019.

## <a name="example"></a>Ejemplo

Este ejemplo contiene la primera definición.

```c
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4744.

```c
// C4744b.c
// compile with: C4744.c /GL /W1
// C4744 expected
#include <stdio.h>

extern unsigned global;

main()
{
    printf_s("%d\n", global);
}
```
