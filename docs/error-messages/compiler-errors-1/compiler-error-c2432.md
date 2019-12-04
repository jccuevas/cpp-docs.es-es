---
title: Error del compilador C2432
ms.date: 11/04/2016
f1_keywords:
- C2432
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
ms.openlocfilehash: d4234626bc246d6da87be68b03d44562dd5990ff
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744516"
---
# <a name="compiler-error-c2432"></a>Error del compilador C2432

referencia no válida a datos de 16 bits en ' Identifier '

Un registro de 16 bits se usa como índice o registro base. El compilador no admite la referencia a datos de 16 bits. los registros de 16 bits no se pueden usar como registros de índice o base al compilar para código de 32 bits.

En el ejemplo siguiente se genera C2432:

```cpp
// C2432.cpp
// processor: x86
int main() {
   _asm mov eax, DWORD PTR [bx]   // C2432
}
```
