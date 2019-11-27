---
title: ADVERTENCIA del compilador (nivel 4) C4032
ms.date: 11/04/2016
f1_keywords:
- C4032
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
ms.openlocfilehash: 52e80340a5157e9350b6d4bbf3bcabea0487e089
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541256"
---
# <a name="compiler-warning-level-4-c4032"></a>ADVERTENCIA del compilador (nivel 4) C4032

el parámetro formal ' número ' tiene un tipo diferente cuando se promueve

El tipo de parámetro no es compatible, a través de promociones predeterminadas, con el tipo en una declaración anterior.

Se trata de un error en ANSI C ([/za](../../build/reference/za-ze-disable-language-extensions.md)) y una advertencia en las extensiones de Microsoft (/ZE).

## <a name="example"></a>Ejemplo

```c
// C4032.c
// compile with: /W4
void func();
void func(char);   // C4032, char promotes to int

int main()
{
}
```