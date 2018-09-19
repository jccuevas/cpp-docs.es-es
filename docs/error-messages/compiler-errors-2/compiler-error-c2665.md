---
title: Error del compilador C2665 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2665
dev_langs:
- C++
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b442e1de0481ef3d00742ed201575526332decff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109150"
---
# <a name="compiler-error-c2665"></a>Error del compilador C2665

'function': ninguna de las sobrecargas número1 puede convertir el parámetro número2 del tipo 'tipo'

Un parámetro de la función sobrecargada no se puede convertir al tipo requerido.  Soluciones posibles:

- Proporcione un operador de conversión.

- Utilice una conversión explícita.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2665.

```
// C2665.cpp
void func(short, char*){}
void func(char*, char*){}

int main() {
   func(0, 1);   // C2665
   func((short)0, (char*)1);   // OK
}
```