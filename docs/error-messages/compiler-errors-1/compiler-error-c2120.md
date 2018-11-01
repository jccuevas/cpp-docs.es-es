---
title: Error del compilador C2120
ms.date: 11/04/2016
f1_keywords:
- C2120
helpviewer_keywords:
- C2120
ms.assetid: b0f3f66c-6cd2-4f48-9ea3-c270b53c2b8c
ms.openlocfilehash: 699a80b2cdb1de175c78efb918ba9389ec3695f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486299"
---
# <a name="compiler-error-c2120"></a>Error del compilador C2120

'void' no es válido con todos los tipos

El `void` tipo se utiliza en una declaración con otro tipo.

El ejemplo siguiente genera C2120:

```
// C2120.cpp
int main() {
   void int i;   // C2120
   int j;   // OK
}
```