---
title: Compilador advertencia (nivel 4) C4238 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4238
dev_langs:
- C++
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4d5f358d08f81e6b8097140ad47d54f4b3b3fed
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057033"
---
# <a name="compiler-warning-level-4-c4238"></a>Advertencia del compilador (nivel 4) C4238

ha utilizado una extensión no estándar: valor-r de clase utilizado como valor l

Para ofrecer compatibilidad con versiones anteriores de Visual C++, las extensiones de Microsoft (**/Ze**) le permiten usar un tipo de clase como un valor r en un contexto que implícita o explícitamente tome su dirección. En algunos casos, como en el ejemplo siguiente, esto puede ser peligroso.

## <a name="example"></a>Ejemplo

```
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

Este uso produce un error en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).