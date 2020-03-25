---
title: Advertencia del compilador (nivel 4) C4214
ms.date: 11/04/2016
f1_keywords:
- C4214
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
ms.openlocfilehash: 70dadb7d424352fbde8c5904053b22fe7cc6b77e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161287"
---
# <a name="compiler-warning-level-4-c4214"></a>Advertencia del compilador (nivel 4) C4214

se ha utilizado una extensión no estándar: tipos de campo de bits distintos de int

Con las extensiones de Microsoft (/ZE) predeterminadas, los miembros de la estructura de bits de bits pueden ser de cualquier tipo entero.

## <a name="example"></a>Ejemplo

```c
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

Estos campos de bits no son válidos con compatibilidad con ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).
