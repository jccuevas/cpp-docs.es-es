---
title: Compilador advertencia (nivel 1) C4744 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4744
dev_langs:
- C++
helpviewer_keywords:
- C4744
ms.assetid: f2a7d0b5-afd5-4926-abc3-cfbd367e3ff5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1754977486327e06fb56a786be523c1b2fb7b917
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068980"
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