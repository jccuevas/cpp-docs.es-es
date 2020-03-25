---
title: ADVERTENCIA del compilador (nivel 4) C4032
ms.date: 11/04/2016
f1_keywords:
- C4032
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
ms.openlocfilehash: 84bfef28de2899a216616a6a5d9fb15422f2afec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185417"
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
