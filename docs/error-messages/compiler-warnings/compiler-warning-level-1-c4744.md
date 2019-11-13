---
title: ADVERTENCIA del compilador (nivel 1) C4744
ms.date: 11/04/2016
f1_keywords:
- C4744
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
ms.openlocfilehash: f6954ae7966edf200249bb5d10f0dfb011bcef22
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051559"
---
# <a name="compiler-warning-level-1-c4744"></a>ADVERTENCIA del compilador (nivel 1) C4744

' var ' tiene un tipo diferente en ' archivo1 ' y ' archivo2 ': ' tipo1 ' y ' tipo2 '

Una variable externa a la que se hace referencia o que se define en dos archivos tiene tipos diferentes en esos archivos.  Para resolverlo, haga que las definiciones de tipo sean iguales o cambie el nombre de la variable en uno de los archivos.

C4744 solo se emite cuando los archivos se compilan con/GL.  Para obtener más información, consulte [/GL (Optimización de todo el programa)](../../build/reference/gl-whole-program-optimization.md).

> [!NOTE]
>  C4744 suele producirse en archivos C C++(no), porque C++ en un nombre de variable se decora con información de tipo.  Cuando el ejemplo (a continuación) se compila como C++, obtendrá el error del vinculador LNK2019.

## <a name="example"></a>Ejemplo

Este ejemplo contiene la primera definición.

```c
// C4744.c
// compile with: /c /GL
int global;
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4744.

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