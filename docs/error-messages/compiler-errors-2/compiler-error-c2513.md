---
title: Error del compilador C2513 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2513
dev_langs:
- C++
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82df537e49ca17140d70977486314f43a072022d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045437"
---
# <a name="compiler-error-c2513"></a>Error del compilador C2513

'type': ninguna variable declarada antes de '='

El especificador de tipo aparece en la declaración de variable sin un identificador.

El ejemplo siguiente genera C2513:

```
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

Este error también puede generarse como resultado de un trabajo de conformidad del compilador realizado para Visual Studio .NET 2003: inicialización de una definición de tipo ya no se permite. La inicialización de una definición de tipo no está permitida por el estándar y genera ahora un error del compilador.

```
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

Una alternativa sería eliminar `typedef` definir una variable con la lista de inicializadores agregado, pero esto no se recomienda porque creará una variable con el mismo nombre que el tipo y ocultar el nombre de tipo.