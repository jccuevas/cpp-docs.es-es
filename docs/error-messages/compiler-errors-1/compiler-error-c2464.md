---
title: Error del compilador C2464 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2464
dev_langs:
- C++
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff74085364d6638772ab2376aace93fea741056b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103150"
---
# <a name="compiler-error-c2464"></a>Error del compilador C2464

'identifier': no se puede utilizar 'new' para asignar una referencia

Se ha asignado un identificador de referencia con el `new` operador. Las referencias no son objetos de memoria, por lo que `new` no puede devolver un puntero a ellos. Use la sintaxis de declaración de variable estándar para declarar una referencia.

El ejemplo siguiente genera C2464:

```
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```