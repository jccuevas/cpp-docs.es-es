---
title: Advertencia del compilador (nivel 4) C4629
ms.date: 11/04/2016
f1_keywords:
- C4629
helpviewer_keywords:
- C4629
ms.assetid: 158cde12-bae5-4d43-b575-b52b35aaa0b9
ms.openlocfilehash: db3f4201dbf5ff925449b0924d08a43ee4283b3e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408048"
---
# <a name="compiler-warning-level-4-c4629"></a>Advertencia del compilador (nivel 4) C4629

Dígrafo usado, secuencia de caracteres 'dígrafo' interpretada como token 'char' (inserte un espacio entre los dos caracteres si no es lo que tenía previsto)

En [/Za](../../build/reference/za-ze-disable-language-extensions.md), el compilador le advierte cuando detecta un dígrafo.

El ejemplo siguiente genera la advertencia C4629:

```
// C4629.cpp
// compile with: /Za /W4
int main()
<%   // C4629 <% digraph for {
}
```