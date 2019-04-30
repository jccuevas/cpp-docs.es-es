---
title: Compilador advertencia (nivel 4) C4032
ms.date: 11/04/2016
f1_keywords:
- C4032
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
ms.openlocfilehash: fa1602d63ed9822725fea8e1b842929f221d3926
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401467"
---
# <a name="compiler-warning-level-4-c4032"></a>Compilador advertencia (nivel 4) C4032

parámetro formal 'número' tiene un tipo diferente cuando promueve

El tipo de parámetro no es compatible mediante promociones predeterminadas con el tipo de una declaración anterior.

Se trata de un error en ANSI C ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) y una advertencia en las extensiones de Microsoft (/Ze).

## <a name="example"></a>Ejemplo

```
// C4032.c
// compile with: /W4
void func();
void func(char);   // C4032, char promotes to int

int main()
{
}
```