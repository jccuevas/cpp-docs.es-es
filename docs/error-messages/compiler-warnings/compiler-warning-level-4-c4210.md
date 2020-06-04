---
title: Advertencia del compilador (nivel 4) C4210
ms.date: 11/04/2016
f1_keywords:
- C4210
helpviewer_keywords:
- C4210
ms.assetid: f8600adf-dfe2-4022-a37a-3d4997641dfd
ms.openlocfilehash: e37ff1fbcfd2ad4088a94204374b33c2c103797c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161326"
---
# <a name="compiler-warning-level-4-c4210"></a>Advertencia del compilador (nivel 4) C4210

se ha utilizado una extensión no estándar: el ámbito de archivo dado

Con las extensiones de Microsoft ([/ze](../../build/reference/za-ze-disable-language-extensions.md)) predeterminadas, las declaraciones de función tienen ámbito de archivo.

```c
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

Esta extensión puede impedir que el código sea portable a otros compiladores.
