---
title: Advertencia del compilador (nivel 4) C4210
ms.date: 11/04/2016
f1_keywords:
- C4210
helpviewer_keywords:
- C4210
ms.assetid: f8600adf-dfe2-4022-a37a-3d4997641dfd
ms.openlocfilehash: 3435e18f60568cad390dcb0ef7900658a21ea959
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638729"
---
# <a name="compiler-warning-level-4-c4210"></a>Advertencia del compilador (nivel 4) C4210

extensión no estándar utilizada: función recibido ámbito de archivo

Con las extensiones de Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)), las declaraciones de función tienen ámbito de archivo.

```
// C4210.c
// compile with: /W4 /c
void func1()
{
   extern int func2( double );   // C4210 expected
}

int main()
{
   func2( 4 );   //  /Ze passes 4 as type double
}                //  /Za passes 4 as type int
```

Esta extensión puede impedir que el código que se va a otros compiladores.