---
title: Error del compilador C2432
ms.date: 11/04/2016
f1_keywords:
- C2432
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
ms.openlocfilehash: e2983d966a6290ce19713c63feb502c8ffc74bf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631256"
---
# <a name="compiler-error-c2432"></a>Error del compilador C2432

referencia no válida a datos de 16 bits en 'identifier'

Un registro de 16 bits se usa como un índice o el registro de base. El compilador no es compatible con la que hacen referencia a datos de 16 bits. registros de 16 bits no se puede usar como base o índice registros cuando se compila para código de 32 bits.

El ejemplo siguiente genera C2432:

```
// C2432.cpp
// processor: x86
int main() {
   _asm mov eax, DWORD PTR [bx]   // C2432
}
```