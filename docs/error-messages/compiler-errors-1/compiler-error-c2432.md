---
title: Error del compilador C2432 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2432
dev_langs:
- C++
helpviewer_keywords:
- C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ca8c2c62415b6ec3c29c820a23677a87a2695c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055915"
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