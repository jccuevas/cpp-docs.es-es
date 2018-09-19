---
title: Error del compilador C2541 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2541
dev_langs:
- C++
helpviewer_keywords:
- C2541
ms.assetid: ed95180f-00df-4e62-a8e9-1b6dab8281bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 492f6f938af5e09221bff3c1c848c9688b28931d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049155"
---
# <a name="compiler-error-c2541"></a>Error del compilador C2541

'delete': delete: no se puede eliminar los objetos que no sean punteros

El [eliminar](../../cpp/delete-operator-cpp.md) se usó el operador en un objeto que no es un puntero.

El ejemplo siguiente genera C2541:

```
// C2541.cpp
int main() {
   int i;
   delete i;   // C2541 i not a pointer

   // OK
   int *ip = new int;
   delete ip;
}
```