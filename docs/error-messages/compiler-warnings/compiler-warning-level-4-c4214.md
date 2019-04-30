---
title: Advertencia del compilador (nivel 4) C4214
ms.date: 11/04/2016
f1_keywords:
- C4214
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
ms.openlocfilehash: 31711d3709b7c2ae3658d760f538ea9e841d33a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401129"
---
# <a name="compiler-warning-level-4-c4214"></a>Advertencia del compilador (nivel 4) C4214

ha utilizado una extensión no estándar: tipos de campo que no sea de tipo int de bits

Con las extensiones de Microsoft (/Ze) de forma predeterminada, los miembros de estructura de campo de bits pueden ser de cualquier tipo entero.

## <a name="example"></a>Ejemplo

```
// C4214.c
// compile with: /W4
struct bitfields
{
   unsigned short j:4;  // C4214
};

int main()
{
}
```

Estos campos de bits no son válidas en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).