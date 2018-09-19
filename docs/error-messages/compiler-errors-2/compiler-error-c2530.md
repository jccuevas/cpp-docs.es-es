---
title: Error del compilador C2530 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2530
dev_langs:
- C++
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f41f9ec64e2074ed5e0cd2654f2b6bfec886bc07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103200"
---
# <a name="compiler-error-c2530"></a>Error del compilador C2530

'identifier': se deben inicializar referencias

Debe inicializar una referencia cuando se declara, a menos que ya se haya declarado:

- Con la palabra clave [extern](../../cpp/using-extern-to-specify-linkage.md).

- Como miembro de una clase, estructura o unión (y se inicializa en el constructor).

- Como un parámetro en una definición o declaración de función.

- Como el tipo de valor devuelto de una función.

El ejemplo siguiente genera C2530:

```
// C2530.cpp
int main() {
   int i = 0;
   int &j;   // C2530
   int &k = i;   // OK
}
```