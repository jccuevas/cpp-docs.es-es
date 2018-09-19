---
title: Compilador advertencia (nivel 2) C4094 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4094
dev_langs:
- C++
helpviewer_keywords:
- C4094
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b9317cbc31ef8bddb14da11af1087a148fd3188
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078717"
---
# <a name="compiler-warning-level-2-c4094"></a>Compilador advertencia (nivel 2) C4094

sin etiquetas 'token' no ha declarado símbolos

El compilador detectó una declaración vacía con una estructura no etiquetado, unión o clase. Se omite la declaración.

## <a name="example"></a>Ejemplo

```
// C4094.cpp
// compile with: /W2
struct
{
};   // C4094

int main()
{
}
```

Esta condición genera un error en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).