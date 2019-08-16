---
title: Advertencia del compilador (nivel 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: 2118a32af8b99d35c1e1a6691561391ec5d2b8cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385425"
---
# <a name="compiler-warning-level-1-c4744"></a>Advertencia del compilador (nivel 1) C4744

'var' tiene un tipo diferente en 'archivo1' y 'archivo2': 'type1' y 'type2'

Una variable externa que hace referencia o definido en dos archivos tiene distintos tipos de esos archivos.  Para resolver, hacer que las definiciones de tipo la misma, o cambiar el nombre de variable en uno de los archivos.

Se emite C4744 solo cuando los archivos se compilan con/GL.  Para obtener más información, consulte [/GL (Optimización de todo el programa)](../../build/reference/gl-whole-program-optimization.md).

> [!NOTE]
>  C4744 aparece normalmente en los archivos de C (no de C++), porque en C++, un nombre de variable está decorado con información de tipo.  Cuando el ejemplo (abajo) se compila como C++, obtendrá el error del vinculador LNK2019.

## <a name="example"></a>Ejemplo

Este ejemplo contiene la primera definición.

```
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4744.

```
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