---
title: Compilador advertencia (nivel 1) C4804 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4804
dev_langs:
- C++
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd1d1659ad6c8716cebf37a99f234af7b41f5745
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094811"
---
# <a name="compiler-warning-level-1-c4804"></a>Advertencia del compilador (nivel 1) C4804

'operación': uso no seguro del tipo 'bool' en la operación

Esta advertencia es para cuando usa un `bool` variable o un valor de forma inesperada. Por ejemplo, se genera C4804 si usa operadores como el operador unario negativo (**-**) o el operador de complemento (`~`). El compilador evalúa la expresión.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4804:

```
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```